---
title: "FreeNX initial connection slow"
date: 2011-11-16
forum: General Help
---

### Post by padpad on 2011-11-16
I´m experiencing a problem under kubuntu 10.04 with Freenx. The connection authentication is quite normal and after about 20 seconds the connection seems to be established but the nxclient show a message "Established display connection" which stucks about 40 seconds until the remote desktop is finally displayed. In /var/log/auth.log polkitd logs a message once the remote Desktop is displayed. The nxserver.log is without any errors at all and i can see the succesfully established nx connection after 20 seconds. Any idea what I can do about it? Thanks in advance.

auth.log as you can see the polkitd messages is almost 1 minute after the authentification:
```
Nov 16 10:58:27 localhost sshd[9295]: Accepted publickey for nx from 10.121.0.1 port 50938 ssh2
Nov 16 10:58:35 localhost sshd[9464]: Accepted password for hotline from 127.0.0.1 port 34533 ssh2
Nov 16 10:59:25 localhost polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session9 (system bus name :1.47 [/usr/lib/kde4/libexec/polkit-kde-authentication-agent-1 -session 1078826732000131919110200000124560007_1321359262_781493], object path /org/kde/PolicyKit1/AuthenticationAgent, locale )

```nxserver.log this piece is logged within 20 seconds after start
```
-- NX SERVER START:  - ORIG_COMMAND=
-- NX SERVER START:  - ORIG_COMMAND=
Info: Using fds #4 and #3 for communication with nxnode.
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: hotline
NX> 102 Password:
Info: Auth method: ssh hotline@127.0.0.1's password:
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 716 Slave mode started successfully.
nxnode_reader: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
nxnode_reader: NX> 716 finished
nxnode_reader: NX> 1001 Bye.

NX> 103 Welcome to: FQ72210 user: hotline
NX> 105 listsession --user="hotline" --status="suspended,running" --geometry="800x600x24+render" --type="unix-kde"
NX> 127 Sessions list of user 'hotline' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: hotline
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="FQ72210" --type="unix-kde" --geometry="800x576" --client="linux" --keyboard="pc105/de" --screeninfo="800x576x24+render"

Info: Using /etc/nxserver/nxacl to change session parameters or deny session.
&link=adsl&backingstore=1&encryption=1&cache=16M&images=64M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=FQ72210&type=unix-kde&geometry=800x576&client=linux&keyboard=pc105/de&screeninfo=800x576x24+render&clientproto=3.2.0&login_method=SSH&user=hotline&userip=10.121.0.1&uniqueid=336EEB5F57B89E496E032919EBDB7472&display=2000&host=127.0.0.1
nxnode_reader: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
server_nxnode_echo: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
nxnode_reader: NX> 700 Session id: FQ72210-2000-336EEB5F57B89E496E032919EBDB7472
nxnode_reader: NX> 705 Session display: 2000
NX> 700 Session id: FQ72210-2000-336EEB5F57B89E496E032919EBDB7472
NX> 705 Session display: 2000
nxnode_reader: NX> 703 Session type: unix-kde
nxnode_reader: NX> 701 Proxy cookie: c931c66fdb58bc2378ee2c7115325136
server_nxnode_echo: NX> 700 Session id: FQ72210-2000-336EEB5F57B89E496E032919EBDB7472
nxnode_reader: NX> 702 Proxy IP: 127.0.0.1
nxnode_reader: NX> 706 Agent cookie: c931c66fdb58bc2378ee2c7115325136
nxnode_reader: NX> 704 Session cache: unix-kde
nxnode_reader: NX> 707 SSL tunneling: 1
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: c931c66fdb58bc2378ee2c7115325136
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: c931c66fdb58bc2378ee2c7115325136
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
server_nxnode_echo: NX> 705 Session display: 2000
server_nxnode_echo: NX> 703 Session type: unix-kde
server_nxnode_echo: NX> 701 Proxy cookie: c931c66fdb58bc2378ee2c7115325136
server_nxnode_echo: NX> 702 Proxy IP: 127.0.0.1
server_nxnode_echo: NX> 706 Agent cookie: c931c66fdb58bc2378ee2c7115325136
server_nxnode_echo: NX> 704 Session cache: unix-kde
server_nxnode_echo: NX> 707 SSL tunneling: 1
nxnode_reader: NX> 1009 Session status: starting
NX> 1009 Session status: starting
nxnode_reader: NX> 710 Session status: running
server_nxnode_echo: NX> 1009 Session status: starting
nxnode_reader: NX> 1002 Commit
nxnode_reader: NX> 1006 Session status: running
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
server_nxnode_echo: NX> 710 Session status: running
server_nxnode_echo: NX> 1002 Commit
session_status 336EEB5F57B89E496E032919EBDB7472 Running
NX> 105 server_nxnode_echo: NX> 1006 Session status: running
bye
Bye
NX> 999 Bye
```

---

