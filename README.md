# Register

Register is a simple Python program I made because I couldn't find my [check
register](https://en.wikipedia.org/wiki/Check_register) after I moved.

The program assumes your currency goes to two decimal places. Otherwise, there 
is no special handling of different currencies. The program is meant to be run
by a single user and it creates and updates a dot-file in the user's home
directory called `.register.data`.

Right now, the usage is very, very simple.

    ./register <entry name> <entry change>

The `entry name` is the event in which you gained or lost money. The `entry
change` is the amount of money which you gained or lost. The gain and losses
are positive (unsigned) or negative (signed) respectively.

Some examples and sample output:

    ./register Payday 1244.34
    ./register Rent -750.00
    ./register "Weekend Trip" -150

    +--------------+----------+-----------+
    | Name         |   Change |   Balance |
    +==============+==========+===========+
    | Gas          |   -45.00 |    551.00 |
    +--------------+----------+-----------+
    | Coffee       |    -1.09 |    549.91 |
    +--------------+----------+-----------+
    | Payday       |  1244.34 |   1794.25 |
    +--------------+----------+-----------+
    | Rent         |  -750.00 |   1044.25 |
    +--------------+----------+-----------+
    | Weekend Trip |  -150.00 |    894.25 |
    +--------------+----------+-----------+

The first entry you make assumes your balance is 0.00 and adds the `entry 
change` to that balance. So, if your first entry looks like `./register Payday
1300` then the output will look like this:

    +--------+----------+-----------+
    | Name   |   Change |   Balance |
    +========+==========+===========+
    | Payday |  1300.00 |   1300.00 |
    +--------+----------+-----------+

Conversely, if your first entry looks like `./register Rent -750`:

    +--------+----------+-----------+
    | Name   |   Change |   Balance |
    +========+==========+===========+
    | Rent   |  -750.00 |   -750.00 |
    +--------+----------+-----------+

# Requirements

This program requires [tabulate](https://pypi.python.org/pypi/tabulate). You
can install tabulate with pip like `pip install tabulate`.
