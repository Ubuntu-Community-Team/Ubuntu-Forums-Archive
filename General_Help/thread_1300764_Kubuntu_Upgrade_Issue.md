---
title: "Kubuntu Upgrade Issue"
date: 2009-10-25
forum: General Help
---

### Post by dh04000 on 2009-10-25
I upgraded from Kubuntu 9.04 to 9.10 and now I have an issue with Akondi server (what ever that is). What does it even do by-the-way? Which applications use it?

Here's the error report. Can someone write me a sudo command to fix the messed up components?

Thanks :)



Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration.
The following drivers are installed: QSQLITE, QMYSQL3, QMYSQL.
Make sure the required driver is installed.

File content of '/home/devin/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL
SizeThreshold=4096
ExternalPayload=false

[QMYSQL]
Name=akonadi
User=
Password=
Options="UNIX_SOCKET=/home/devin/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true


Test 2:  SUCCESS
--------

MySQL server found.
Details: You currently have configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'.
Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld', its locations varies depending on the distribution.

Test 3:  SUCCESS
--------

MySQL server is executable.
Details: MySQL server found: /usr/sbin/mysqld-akonadi  Ver 5.1.37-1ubuntu5 for debian-linux-gnu on i486 ((Ubuntu))


Test 4:  ERROR
--------

MySQL server log contains errors.
Details: The MySQL server error log file &apos;<a href='/home/devin/.local/share/akonadi/db_data/mysql.err'>/home/devin/.local/share/akonadi/db_data/mysql.err</a>&apos; contains errors.

File content of '/home/devin/.local/share/akonadi/db_data/mysql.err':
091025 10:42:58 [Note] Plugin 'FEDERATED' is disabled.
091025 10:42:58  InnoDB: Started; log sequence number 0 44233
091025 10:42:58 [ERROR] Aborting

091025 10:42:58  InnoDB: Starting shutdown...
091025 10:43:00  InnoDB: Shutdown completed; log sequence number 0 44233
091025 10:43:00 [Warning] Forcing shutdown of 1 plugins
091025 10:43:00 [Note] 


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
# log queries slower than n seconds, log file name relative to datadir
log_slow_queries=mysql.slow
long_query_time=1
# log queries not using indices, debug only, disable for production use
log_queries_not_using_indexes=1
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
Details: The MySQL server configuration was found at <a href='/home/devin/.local/share/akonadi/mysql.conf'>/home/devin/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/home/devin/.local/share/akonadi/mysql.conf':
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
# log queries slower than n seconds, log file name relative to datadir
log_slow_queries=mysql.slow
long_query_time=1
# log queries not using indices, debug only, disable for production use
log_queries_not_using_indexes=1
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
Akonadi 1.2.1


Test 9:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 10:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 12:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
distlistresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
microblog.desktop
nepomukcontactfeeder.desktop
nepomukemailfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
strigifeeder.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
distlistresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
microblog.desktop
nepomukcontactfeeder.desktop
nepomukemailfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
strigifeeder.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share'

Test 13:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server did report error during startup into <a href='/home/devin/.local/share/akonadi/akonadiserver.error'>/home/devin/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/devin/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/devin/.local/share/akonadi//mysql.conf", "--datadir=/home/devin/.local/share/akonadi/db_data/", "--socket=/home/devin/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "091025 10:42:58 [Warning] The syntax '--log_slow_queries' is deprecated and will be removed in MySQL 7.0. Please use '--slow_query_log'/'--slow_query_log_file' instead.
091025 10:42:58 [ERROR] Error message file '/usr/share/mysql/english/errmsg.sys' had only 480 error messages,
but it should contain at least 637 error messages.
Check that the above file is the right version for this program!
" 
exit code: 1 
process error: "Process operation timed out" 
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8051f25]
1: akonadiserver [0x80523f6]
2: [0x548400]
3: [0x548422]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x5734d1]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x576932]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0xdb8f8c]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8052f54]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x85) [0xe4b0d5]
9: /usr/lib/libQtCore.so.4 [0xe59ed5]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0xe5b298]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x804dbf3]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x1ab8) [0x227a48]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x70) [0x22a030]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x58) [0x22b3c8]
15: akonadiserver(main+0x362) [0x804d032]
16: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x55fb56]
17: akonadiserver [0x804cc01]
]
" 


Test 14:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/home/devin/.local/share/akonadi/akonadiserver.error.old'>/home/devin/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/devin/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/devin/.local/share/akonadi//mysql.conf", "--datadir=/home/devin/.local/share/akonadi/db_data/", "--socket=/home/devin/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "091025 10:42:56 [Warning] The syntax '--log_slow_queries' is deprecated and will be removed in MySQL 7.0. Please use '--slow_query_log'/'--slow_query_log_file' instead.
091025 10:42:56 [ERROR] Error message file '/usr/share/mysql/english/errmsg.sys' had only 480 error messages,
but it should contain at least 637 error messages.
Check that the above file is the right version for this program!
" 
exit code: 1 
process error: "Process operation timed out" 
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8051f25]
1: akonadiserver [0x80523f6]
2: [0x3c6400]
3: [0x3c6422]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x60d4d1]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x610932]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0x177f8c]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8052f54]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x85) [0x20a0d5]
9: /usr/lib/libQtCore.so.4 [0x218ed5]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0x21a298]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x804dbf3]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x1ab8) [0xcaba48]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x70) [0xcae030]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x58) [0xcaf3c8]
15: akonadiserver(main+0x362) [0x804d032]
16: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x5f9b56]
17: akonadiserver [0x804cc01]
]
" 


Test 15:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 16:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.

---

### Post by lovinglinux on 2009-10-25
I had similar Akonadi problems on one machine and I was unable to disable it, but I was able to disable it on my desktop, where I don't use PIM (Personal Information Management) applications.

These are the applications that probably make use of it:

akregator kaddressbook kalarm kdepim kdepim-groupware kdepim-kresources kdepim-strigi-plugins kdepim-wizards kjots kmail knode knotes konsolekalendar kontact korganizer ktimetracker

> 
From: [http://en.wikipedia.org/wiki/Akonadi](http://en.wikipedia.org/wiki/Akonadi)

Akonadi is a storage service for personal information management (PIM) data and meta data. It is one of the “pillars” (core technologies) behind the KDE 4 project, although it is designed to be used in any desktop environment. It is extensible and provides concurrent read, write, and query access.

Akonadi will provide unique desktop wide object identification and retrieval.[1] Akonadi will function as an extensible data storage for all PIM applications. In KDE 3 each PIM application had different data storage and handling methods, which led to several implementations of essentially the same features. Besides data storage, Akonadi has several other components including search, and a library (cache) for easy access and notification of data changes.

Akonadi communicates with servers to fetch and send data instead of applications through a specialized API. Data can then be retrieved from Akonadi by a model designed to collect a specific data (mail, calendar, contacts, etc). The application itself will be made of viewers and editors to display data to the user and let them input data. Akonadi will also support metadata created by applications.[2]

Because Akonadi takes care of data storage and retrieval, which are traditionally the difficult parts of creating a PIM application, development of PIM applications is made much easier. In fact, the Mailody team demonstrated how a mail reader could be created in only 10 minutes using Akonadi.[3]

---

### Post by dh04000 on 2009-10-25
How do I keep Akonadi from autostarting at loggin? I can stop using most of those applications (I don't think I use them now).

---

### Post by lovinglinux on 2009-10-25
> **dh04000 said:**
> How do I keep Akonadi from autostarting at loggin? I can stop using most of those applications (I don't think I use them now).

I have disabled it with [bum](apt:bum).

---

### Post by dh04000 on 2009-10-25
I installed bum, what is the akonadi service called on the list?

---

### Post by lovinglinux on 2009-10-25
> **dh04000 said:**
> I installed bum, what is the akonadi service called on the list?

Strike that :oops:

Sorry, I thought I  have disabled it with bum. But I just checked and it's not operational and it gives the same errors as yours. I guess the problem is that we don't have any applications that makes use of it. See quote below:

> No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

---

### Post by lovinglinux on 2009-10-25
Try to rename the akonadi config files under ~/.kde/share/config and reboot. I think akonadi will be reconfigured and will start properly. I was experiencing plasma issues, so I tried to rename the entire config folder and akonadi started properly after reboot.

---

