HTTOP
=====

Http Top: Small script that ouputs the CPU usage of the HTTP queries served by apache in a 'top' like fashion. Highly useful for debugging overload issues.


It works by taking a snapshot with 'top' as well as reading the server-status (mod_status needs to be enabled) and merging that data in a nice, useful table.


Requirements
============

First and foremost, it needs mod_status enabled with ExtendedStatus On.
Example:

```
ExtendedStatus On

<Location /server-status>
    SetHandler server-status
    Order deny,allow
    Deny from all
    Allow from 127.0.0.1
</Location>
```


It's a perl script, so it will obviously need perl. It needs the 'watch' and the 'column' command line tools as well, but chances are you already have them.


Syntax
======

```
httop [-<1|2>]

-1  List header and values, separated by tabs
-2  List header and values, in a nice table formated with column -ts $'\t'

With no option it starts running 'watch' on option -2
```
