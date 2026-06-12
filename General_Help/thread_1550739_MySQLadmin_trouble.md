---
title: "MySQLadmin trouble:"
date: 2010-08-11
forum: General Help
---

### Post by lordbux on 2010-08-11
I am having trouble with my MySQLadmin ...

*Note: all necessary tools have been installed and PhpMyadmin works fine.*

when i us the command: 
```
mysqladmin -h localhost -u root -p <password>
```

It asks for the password once more and then it says it do not know the command which is actually the password
```

Enter password:
mysqladmin: Unknown command: '<password>'

```

If i just use:
```
mysqladmin -h localhost -u root -p
```
OR
```
mysqladmin -h localhost -u root
```

i simply get the help message as shown below:
```
mysqladmin  Ver 8.42 Distrib 5.1.41, for debian-linux-gnu on i486
Copyright 2000-2008 MySQL AB, 2008 Sun Microsystems, Inc.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Administration program for the mysqld daemon.
Usage: mysqladmin [OPTIONS] command command....
  -c, --count=#       Number of iterations to make. This works with -i
                      (--sleep) only.
  --debug-check       Check memory and open file usage at exit .
  --debug-info        Print some debug info at exit.
  -f, --force         Don't ask for confirmation on drop database; with
                      multiple commands, continue even if an error occurs.
  -C, --compress      Use compression in server/client protocol.
  --character-sets-dir=name 
                      Directory where character sets are.
  --default-character-set=name 
                      Set the default character set.
  -?, --help          Display this help and exit.
  -h, --host=name     Connect to host.
  -b, --no-beep       Turn off beep on error.
  -p, --password[=name] 
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty.
  -P, --port=#        Port number to use for connection or 0 for default to, in
                      order of preference, my.cnf, $MYSQL_TCP_PORT,
                      /etc/services, built-in default (3306).
  --protocol=name     The protocol of connection (tcp,socket,pipe,memory).
  -r, --relative      Show difference between current and previous values when
                      used with -i. Currently works only with extended-status.
  -O, --set-variable=name 
                      Change the value of a variable. Please note that this
                      option is deprecated; you can set variables directly with
                      --variable-name=value.
  -s, --silent        Silently exit if one can't connect to server.
  -S, --socket=name   Socket file to use for connection.
  -i, --sleep=#       Execute commands again and again with a sleep between.
  --ssl               Enable SSL for connection (automatically enabled with
                      other flags). Disable with --skip-ssl.
  --ssl-ca=name       CA file in PEM format (check OpenSSL docs, implies
                      --ssl).
  --ssl-capath=name   CA directory (check OpenSSL docs, implies --ssl).
  --ssl-cert=name     X509 cert in PEM format (implies --ssl).
  --ssl-cipher=name   SSL cipher to use (implies --ssl).
  --ssl-key=name      X509 key in PEM format (implies --ssl).
  --ssl-verify-server-cert 
                      Verify server's "Common Name" in its cert against
                      hostname used when connecting. This option is disabled by
                      default.
  -u, --user=name     User for login if not current user.
  -v, --verbose       Write more information.
  -V, --version       Output version information and exit.
  -E, --vertical      Print output vertically. Is similar to --relative, but
                      prints output vertically.
  -w, --wait[=#]      Wait and retry if connection is down.
  --connect_timeout=# 
  --shutdown_timeout=# 

Variables (--variable-name=value)
and boolean options {FALSE|TRUE}  Value (after reading options)
--------------------------------- -----------------------------
count                             0
debug-check                       FALSE
debug-info                        FALSE
force                             FALSE
compress                          FALSE
character-sets-dir                (No default value)
default-character-set             (No default value)
host                              localhost
no-beep                           FALSE
port                              3306
relative                          FALSE
socket                            /var/run/mysqld/mysqld.sock
sleep                             0
ssl                               FALSE
ssl-ca                            (No default value)
ssl-capath                        (No default value)
ssl-cert                          (No default value)
ssl-cipher                        (No default value)
ssl-key                           (No default value)
ssl-verify-server-cert            FALSE
user                              root
verbose                           FALSE
vertical                          FALSE
connect_timeout                   43200
shutdown_timeout                  3600

Default options are read from the following files in the given order:
/etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf 
The following groups are read: mysqladmin client
The following options may be given as the first argument:
--print-defaults	Print the program argument list and exit
--no-defaults		Don't read default options from any options file
--defaults-file=#	Only read default options from the given file #
--defaults-extra-file=# Read this file after the global files are read

Where command is a one or more of: (Commands may be shortened)
  create databasename	Create a new database
  debug			Instruct server to write debug information to log
  drop databasename	Delete a database and all its tables
  extended-status       Gives an extended status message from the server
  flush-hosts           Flush all cached hosts
  flush-logs            Flush all logs
  flush-status		Clear status variables
  flush-tables          Flush all tables
  flush-threads         Flush the thread cache
  flush-privileges      Reload grant tables (same as reload)
  kill id,id,...	Kill mysql threads
  password new-password Change old password to new-password, MySQL 4.1 hashing.
  old-password new-password Change old password to new-password in old format.

  ping			Check if mysqld is alive
  processlist		Show list of active threads in server
  reload		Reload grant tables
  refresh		Flush all tables and close and open logfiles
  shutdown		Take server down
  status		Gives a short status message from the server
  start-slave		Start slave
  stop-slave		Stop slave
  variables             Prints variables available
  version		Get version info from server

```

This makes no sense, Please help me with this.:( :(

---

### Post by hudsonl on 2010-08-11
You should NOT have a space between the command line arguments -u and -p and the values you are passing ... for example:


mysqladmin -h localhost -**uroot -pMyPassword** ping

Also ... Are you wanting to run mysqladmin or just mysql ... the mysqladmin expects a command at the end ... like ping, flush-table, shutdown, etc.


mysql -h localhost -uroot -pMyPassword

mysql>show databases;

---

### Post by lordbux on 2010-08-11
> **hudsonl said:**
> You should NOT have a space between the command line arguments -u and -p and the values you are passing ... for example:


mysqladmin -h localhost -**uroot -pMyPassword** ping

Also ... Are you wanting to run mysqladmin or just mysql ... the mysqladmin expects a command at the end ... like ping, flush-table, shutdown, etc.


mysql -h localhost -uroot -pMyPassword

mysql>show databases;

Thanks..that woked

---

