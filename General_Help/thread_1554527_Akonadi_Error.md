---
title: "Akonadi Error"
date: 2010-08-16
forum: General Help
---

### Post by JustinAlf on 2010-08-16
My God, I cannot for the life of me figure this out.  Please help!!!!

Here is my error log:


Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/home/justin/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL
SizeThreshold=4096
ExternalPayload=false

[QMYSQL]
Name=akonadi
Host=
User=
Password=
Options="UNIX_SOCKET=/home/justin/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true

[Debug]
Tracer=null


Test 2:  SUCCESS
--------

MySQL server found.
Details: You currently have configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'.
Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld', its locations varies depending on the distribution.

Test 3:  SUCCESS
--------

MySQL server is executable.
Details: MySQL server found: /usr/sbin/mysqld-akonadi  Ver 5.1.41-3ubuntu11 for debian-linux-gnu on i486 ((Ubuntu))


Test 4:  SUCCESS
--------

MySQL server log contains no errors.
Details: The MySQL server log file &apos;<a href='/home/justin/.local/share/akonadi/db_data/mysql.err'>/home/justin/.local/share/akonadi/db_data/mysql.err</a>&apos; does not contain any errors or warnings.

File content of '/home/justin/.local/share/akonadi/db_data/mysql.err':
100816 19:32:36 [Note] Plugin 'FEDERATED' is disabled.
100816 19:32:36  InnoDB: Started; log sequence number 0 134050
100816 19:32:37 [Note] /usr/sbin/mysqld-akonadi: ready for connections.
Version: '5.1.41-3ubuntu11-log'  socket: '/home/justin/.local/share/akonadi/db_misc/mysql.socket'  port: 0  (Ubuntu)


Test 5:  SUCCESS
--------

MySQL server default configuration found.
Details: The default configuration for the MySQL server was found and is readable at <a href='/etc/akonadi/mysql-global.conf'>/etc/akonadi/mysql-global.conf</a>.

File content of '/etc/akonadi/mysql-global.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]
skip_grant_tables
skip_networking

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
#sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
#sql_mode=strict_trans_tables

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
# case-insensitive table names, avoids trouble on windows
lower_case_table_names=1
character_set_server=latin1
collation_server=latin1_general_ci
table_cache=200
thread_cache_size=3
log_bin=mysql-bin
expire_logs_days=3
#sync_bin_log=0
# error log file name, relative to datadir
log_error=mysql.err
log_warnings=2
# log all queries, useful for debugging but generates an enormous amount of data
#log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
#log_slow_queries=mysql.slow
#long_query_time=1
# log queries not using indices, debug only, disable for production use
#log_queries_not_using_indexes=1
# maximum blob size
max_allowed_packet=32M
max_connections=256
# makes sense when having the same query multiple times
# makes no sense with prepared statements and/or transactions
query_cache_type=0
query_cache_size=0

innodb_file_per_table=1
innodb_log_buffer_size=1M
innodb_additional_mem_pool_size=1M
# messure database size and adjust
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
innodb_buffer_pool_size=80M
# size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
innodb_log_file_size=64M
innodb_flush_log_at_trx_commit=2



Test 6:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 7:  SUCCESS
--------

MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href='/home/justin/.local/share/akonadi/mysql.conf'>/home/justin/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/home/justin/.local/share/akonadi/mysql.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]
skip_grant_tables
skip_networking

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
#sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
#sql_mode=strict_trans_tables

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
# case-insensitive table names, avoids trouble on windows
lower_case_table_names=1
character_set_server=latin1
collation_server=latin1_general_ci
table_cache=200
thread_cache_size=3
log_bin=mysql-bin
expire_logs_days=3
#sync_bin_log=0
# error log file name, relative to datadir
log_error=mysql.err
log_warnings=2
# log all queries, useful for debugging but generates an enormous amount of data
#log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
#log_slow_queries=mysql.slow
#long_query_time=1
# log queries not using indices, debug only, disable for production use
#log_queries_not_using_indexes=1
# maximum blob size
max_allowed_packet=32M
max_connections=256
# makes sense when having the same query multiple times
# makes no sense with prepared statements and/or transactions
query_cache_type=0
query_cache_size=0

innodb_file_per_table=1
innodb_log_buffer_size=1M
innodb_additional_mem_pool_size=1M
# messure database size and adjust
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
innodb_buffer_pool_size=80M
# size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
innodb_log_file_size=64M
innodb_flush_log_at_trx_commit=2



Test 8:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.3.1


Test 9:  SUCCESS
--------

Akonadi control process registered at D-Bus.
Details: The Akonadi control process is registered at D-Bus which typically indicates it is operational.

Test 10:  SUCCESS
--------

Akonadi server process registered at D-Bus.
Details: The Akonadi server process is registered at D-Bus which typically indicates it is operational.

Test 11:  SUCCESS
--------

Nepomuk search service registered at D-Bus.
Details: The Nepomuk search service is registered at D-Bus which typically indicates it is operational.

Test 12:  SUCCESS
--------

Nepomuk search service uses an appropriate backend. 
Details: The Nepomuk search service uses one of the recommended backends.

Test 13:  SUCCESS
--------

Server protocol version is recent enough.
Details: The server Protocol version is 23, which equal or newer than the required version 23.

Test 14:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
gcalresource.desktop
googledataresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
gcalresource.desktop
googledataresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share'

Test 15:  SUCCESS
--------

No current Akonadi server error log found.
Details: The Akonadi server did not report any errors during its current startup.

Test 16:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/home/justin/.local/share/akonadi/akonadiserver.error.old'>/home/justin/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/justin/.local/share/akonadi/akonadiserver.error.old':
Control process died, committing suicide! 


Test 17:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 18:  ERROR
--------

Previous Akonadi control error log found.
Details: The Akonadi control process did report error during its previous startup into <a href='/home/justin/.local/share/akonadi/akonadi_control.error.old'>/home/justin/.local/share/akonadi/akonadi_control.error.old</a>.

File content of '/home/justin/.local/share/akonadi/akonadi_control.error.old':
D-Bus session bus went down - quitting

---

### Post by JustinAlf on 2010-08-18
*bump*

Any thoughts here?  I can't be the only one with this type of error.....

---

