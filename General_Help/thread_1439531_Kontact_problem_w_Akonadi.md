---
title: "Kontact problem w/ Akonadi"
date: 2010-03-26
forum: General Help
---

### Post by drew boardman on 2010-03-26
Hi all,

Running Kontact and it runs, albeit, really, really slowly and every now and again I get the following error msg when Akonadi server runs (what is this?).  It was a clean brand-new install with Kontact.
******
Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration.
The following drivers are installed: QMYSQL3, QMYSQL.
Make sure the required driver is installed.

File content of '/home/drew/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL
SizeThreshold=4096
ExternalPayload=false

[QMYSQL]
Name=akonadi
User=
Password=
Options="UNIX_SOCKET=/home/drew/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=false
Host=

[Debug]
Tracer=null


Test 2:  SKIP
--------

MySQL server executable not tested.
Details: The current configuration does not require an internal MySQL server.

Test 3:  SKIP
--------

MySQL server error log not tested.
Details: The current configuration does not require an internal MySQL server.

Test 4:  SKIP
--------

MySQL server configuration not tested.
Details: The current configuration does not require an internal MySQL server.

Test 5:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.2.1


Test 6:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 7:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 8:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 9:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share/gnome:/usr/local/share/:/usr/share/', make sure this includes all paths where Akonadi agents are installed to.

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
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
strigifeeder.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share/gnome:/usr/local/share/:/usr/share/'

Test 10:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server did report error during startup into <a href='/home/drew/.local/share/akonadi/akonadiserver.error'>/home/drew/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/drew/.local/share/akonadi/akonadiserver.error':
Unable to open database "Can't connect to local MySQL server through socket '/home/drew/.local/share/akonadi/db_misc/mysql.socket' (111) QMYSQL: Unable to connect" 
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8051f25]
1: akonadiserver [0x80523f6]
2: [0x4ec400]
3: [0x4ec422]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x9904d1]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x993932]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0x155f8c]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8052f54]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x85) [0x1e80d5]
9: /usr/lib/libQtCore.so.4 [0x1f6ed5]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0x1f8298]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x804dbf3]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x5b5) [0xaf6575]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x58) [0xaf73c8]
14: akonadiserver(main+0x362) [0x804d032]
15: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x97cb56]
16: akonadiserver [0x804cc01]
]
" 


Test 11:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/home/drew/.local/share/akonadi/akonadiserver.error.old'>/home/drew/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/drew/.local/share/akonadi/akonadiserver.error.old':
Unable to open database "Can't connect to local MySQL server through socket '/home/drew/.local/share/akonadi/db_misc/mysql.socket' (111) QMYSQL: Unable to connect" 
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8051f25]
1: akonadiserver [0x80523f6]
2: [0x38a400]
3: [0x38a422]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x5d24d1]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x5d5932]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0x155f8c]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8052f54]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x85) [0x1e80d5]
9: /usr/lib/libQtCore.so.4 [0x1f6ed5]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0x1f8298]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x804dbf3]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x5b5) [0x434575]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x58) [0x4353c8]
14: akonadiserver(main+0x362) [0x804d032]
15: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x5beb56]
16: akonadiserver [0x804cc01]
]
" 


Test 12:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 13:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


Thanks for the help.

Drew

---

### Post by drew boardman on 2010-04-01
So I guess nobody knows?

I'll hang around a bit longer and see if anybody uses Kontact.

Drew

---

### Post by Maximus_ARNP on 2010-05-18
Same problem here.

---

### Post by Maximus_ARNP on 2010-05-20
Background: I have used Kaddressbook (Kontact) on Ubuntu for many years. After a fresh install on Ubuntu 10.04 AMD64, I was not able to get Kaddressbook to work because of Akonadi errors. I reinstalled OS couple of times with no success. As a last resort, I tested lived CD mode on Kubuntu 10.04. I grew more hopeless as Kaddressbook failed even in the live-CD mode of Kubuntu 10.04.

After several days of research, I have been able to work around the problems in the following manner. It does not seem to be a permanent fix, but it works for now.  For more detailed explanations, please refer to the **References** cited in here.

I had following errors:

> Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Test 2:  SUCCESS
--------

Test 3:  SUCCESS
--------

Test 4:  ERROR
--------

MySQL server log contains errors.
Details: The MySQL server error log file &apos;<a href='/home/raj/.local/share/akonadi/db_data/mysql.err'>/home/raj/.local/share/akonadi/db_data/mysql.err</a>&apos; contains errors.

File content of '/home/raj/.local/share/akonadi/db_data/mysql.err':
100519 21:19:08 [Note] Plugin 'FEDERATED' is disabled.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
100519 21:19:08  InnoDB: Retrying to lock the first data file
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.


Test 5:  SUCCESS
--------


Test 6:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 7:  SUCCESS
--------

Test 8:  SUCCESS
--------

Test 9:  SUCCESS
--------

Test 10:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  SUCCESS
--------


Test 12:  SUCCESS
--------


Test 13:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 14:  SUCCESS
--------

Test 15:  SUCCESS
--------

Test 16:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/home/raj/.local/share/akonadi/akonadiserver.error.old'>/home/raj/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/raj/.local/share/akonadi/akonadiserver.error.old':
Database error: Cannot open database. 
  Last driver error: "QMYSQL: Unable to connect" 
  Last database error: "Access denied for user 'raj'@'localhost' (using password: NO)" 
Unable to open database "Access denied for user 'raj'@'localhost' (using password: NO) QMYSQL: Unable to connect" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40b739]
1: akonadiserver() [0x40bc7a]
2: /lib/libc.so.6(+0x33af0) [0x7fbf9ba85af0]
3: /lib/libc.so.6(gsignal+0x35) [0x7fbf9ba85a75]
4: /lib/libc.so.6(abort+0x180) [0x7fbf9ba895c0]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7fbf9cc6b844]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40cd88]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7fbf9ccfa417]
8: /usr/lib/libQtCore.so.4(+0x112529) [0x7fbf9cd0c529]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7fbf9cd0d729]
10: akonadiserver(_ZN6QDebugD1Ev+0x49) [0x4071b9]
11: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x55a) [0x7fbf9d0e0eda]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7fbf9d0e1d1a]
13: akonadiserver(main+0x429) [0x406539]
14: /lib/libc.so.6(__libc_start_main+0xfd) [0x7fbf9ba70c4d]
15: akonadiserver() [0x406019]
]
" 


Test 17:  ERROR
--------

Current Akonadi control error log found.
Details: The Akonadi control process did report error during startup into <a href='/home/raj/.local/share/akonadi/akonadi_control.error'>/home/raj/.local/share/akonadi/akonadi_control.error</a>.

File content of '/home/raj/.local/share/akonadi/akonadi_control.error':
Unable to register service as org.freedesktop.Akonadi.Control Maybe it's already running? 
"[
0: /usr/bin/akonadi_control(_Z11akBacktracev+0x39) [0x416779]
1: /usr/bin/akonadi_control() [0x416cba]
2: /lib/libc.so.6(+0x33af0) [0x7ff5ffb7faf0]
3: /lib/libc.so.6(gsignal+0x35) [0x7ff5ffb7fa75]
4: /lib/libc.so.6(abort+0x180) [0x7ff5ffb835c0]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7ff600d65844]
6: /usr/bin/akonadi_control(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x417dc8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7ff600df4417]
8: /usr/lib/libQtCore.so.4(+0x112529) [0x7ff600e06529]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7ff600e07729]
10: /usr/bin/akonadi_control(main+0x466) [0x42bab6]
11: /lib/libc.so.6(__libc_start_main+0xfd) [0x7ff5ffb6ac4d]
12: /usr/bin/akonadi_control() [0x4120b9]
]
" 


Test 18:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


**I have been able to solve Test 4 Error by following instructions:**

> 
[QUOTE]
sudo aa-complain mysqld
sudo /etc/init.d/apparmor reload

and for safety sake also

sudo aa-complain mysqld-akonadi
sudo /etc/init.d/apparmor reload

and then finally

akonadictl start

**Reference:**
[http://brahmalok.wordpress.com/2010/02/13/akonadi-error-solved/](http://brahmalok.wordpress.com/2010/02/13/akonadi-error-solved/)
[/QUOTE]

**I have been able to solve Test 10, 16 & 17 errors by using following instructions:**

> 
[QUOTE]
Examining your Resources

KRunner offers you Akonadi Resource Configuration, or you can access this through the Akonadi tray icon > Configure. You may find several resources set up. You may find one labelled

Address Book - No KDE address book plugin configured yet.

That's the old compatibility bridge (possibly created by the migrator tool). You should remove this one!

std.vcf - Ready

This is the 'VCard File Resource' which points to $HOME/.kde/share/apps/kabc/std.vcf per default. It is not recommended that you use that one, as it doesn't share the benefit of Akonadi.

Personal Contacts - Offline

That's the preferred resource for your local contacts which points to

 $HOME/.local/share/contacts

Note that this may say 'Offline' when in fact you are using it. This is a display bug, and can safely be ignored.

**Reference:**
[http://userbase.kde.org/Akonadi_and_AddressBook#Examining_your_Resources](http://userbase.kde.org/Akonadi_and_AddressBook#Examining_your_Resources)
[/QUOTE]

**I have been able to solve Test 14 error "no resource agents found" as follows:**

> 
Add following line to the file **.bushrc** in **/home/USERNAME** folder:
[QUOTE]
export XDG_DATA_DIRS="/opt/kde/share/akonady/agents:$XDG_DATA_DIRS"

**Reference**: [http://forum.kde.org/viewtopic.php?f=20&t=85072](http://forum.kde.org/viewtopic.php?f=20&t=85072)
[/QUOTE]

Restart your computer.

At next login, if **Kontact** loads automatically, it may still give you some errors loading **Akonadi** & **Kaddressbook**. So, please exit **Kontact**. Then independently load **Kaddressbook** (Menu ---> Office ----> Kaddressbook). Once, it is loaded, you can exit **Kaddressbook**.  Now reload **Kontact**. Your **Kaddressbook** from inside of **Kontact** should work fine.

Sincerely.

---

### Post by mateuszbaranski on 2010-06-09
I have got also problems with using Kontact because of akonadi errors. I upgraded from 9.10 kubuntu to 10.04 kubuntu.
There are problems from the begining - PIM is the most used feature in linux by me so it is crucial.
I have also tried the live-cd - akonadi does not work there neither.

I have found that it might be the kwallet problem. I noticed that when I open the kwallet manualy before runing akonadi and kontact - everything is fine - I do not have a message "akonadi in not runing" in address book in kontact.

I have also used the procedure mentioned above concerning the:
aa-complain mysql ... etc.

So when I log in, 
1) I start the kwalletmanager. 
2) open my wallet  (klicking on it and giving password to the wallet)
3) run akonadictl start 

And kontact works with kaddress book

A little weird but works....

---

