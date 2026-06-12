---
title: "nxclient 3.x Session failed over 200ms latency connection"
date: 2011-01-22
forum: General Help
---

### Post by lucianodenti on 2011-01-22
I have installed FreeNX server v 0.7.3 from ppa repository.
Connection with the server from windows and linux client over lan connection work, but with a 200ms latency connection (mobile network) all nx client versions fail to bringing up session (Message: 'Session 1.2.3.4 failed').
With QTNX I can enstablish the session with the server without problems but after 90 sec. from login ...


ANY HELP IS APPRECIATED.


System: Ubuntu 10.04 Desktop x86_64
FreeNX server ver. 0.7.3
NX client: all versions 3.2.x, 3.3.x, 3.4.x, all platforms (Windows and linux)



FILE:/var/log/nxserver.log

-- NX SERVER START:  - ORIG_COMMAND=
-- NX SERVER START:  - ORIG_COMMAND=
Info: Using fds #4 and #3 for communication with nxnode.
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: ldxxxxxxx
NX> 102 Password: 
Info: Auth method: ssh ldxxxxxxx@127.0.0.1's password:
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 716 Slave mode started successfully.
nxnode_reader: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
nxnode_reader: NX> 716 finished
nxnode_reader: NX> 1001 Bye.

NX> 103 Welcome to: BG-NMS01 user: ldxxxxxxx
NX> 105 listsession --user="ldxxxxxxx" --status="suspended,running" --geometry="1280x800x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'ldxxxxxxx' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: ldxxxxxxx
NX> 105 startsession  --link="modem" --backingstore="1" --encryption="1" --cache="4M" --images="0M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="1.2.3.4" --type="unix-gnome" --geometry="800x600+240+76" --client="linux" --keyboard="pc105/it" --screeninfo="800x600x24+render" 

Info: Using /etc/nxserver/nxacl to change session parameters or deny session.
Warning: nxagent proxy without .nX2010-lock found on host:port 127.0.0.1:8010.
&link=modem&backingstore=1&encryption=1&cache=4M&images=0M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=1.2.3.4&type=unix-gnome&geometry=800x600+240+76&client=linux&keyboard=pc105/it&screeninfo=800x600x24+render&clientproto=3.2.0&login_method=SSH&user=ldxxxxxxx&userip=5.6.7.8&uniqueid=E549076C3016E9B8407C21660EF0A2E4&display=2046&host=127.0.0.1 
nxnode_reader: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
server_nxnode_echo: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
nxnode_reader: NX> 700 Session id: BG-NMS01-2046-E549076C3016E9B8407C21660EF0A2E4
nxnode_reader: NX> 705 Session display: 2046
nxnode_reader: NX> 703 Session type: unix-gnome
nxnode_reader: NX> 701 Proxy cookie: 3867075b76f0f649c80742faedfc888b
nxnode_reader: NX> 702 Proxy IP: 127.0.1.1
nxnode_reader: NX> 706 Agent cookie: 3867075b76f0f649c80742faedfc888b
nxnode_reader: NX> 704 Session cache: unix-gnome
nxnode_reader: NX> 707 SSL tunneling: 1
NX> 700 Session id: BG-NMS01-2046-E549076C3016E9B8407C21660EF0A2E4
NX> 705 Session display: 2046
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 3867075b76f0f649c80742faedfc888b
NX> 702 Proxy IP: 127.0.1.1
NX> 706 Agent cookie: 3867075b76f0f649c80742faedfc888b
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
server_nxnode_echo: NX> 700 Session id: BG-NMS01-2046-E549076C3016E9B8407C21660EF0A2E4
server_nxnode_echo: NX> 705 Session display: 2046
server_nxnode_echo: NX> 703 Session type: unix-gnome
server_nxnode_echo: NX> 701 Proxy cookie: 3867075b76f0f649c80742faedfc888b
server_nxnode_echo: NX> 702 Proxy IP: 127.0.1.1
server_nxnode_echo: NX> 706 Agent cookie: 3867075b76f0f649c80742faedfc888b
server_nxnode_echo: NX> 704 Session cache: unix-gnome
server_nxnode_echo: NX> 707 SSL tunneling: 1
nxnode_reader: NX> 1009 Session status: starting
nxnode_reader: NX> 710 Session status: running
nxnode_reader: NX> 1002 Commit
nxnode_reader: NX> 1006 Session status: running
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
server_nxnode_echo: NX> 1009 Session status: starting
server_nxnode_echo: NX> 710 Session status: running
server_nxnode_echo: NX> 1002 Commit
session_status E549076C3016E9B8407C21660EF0A2E4 Running
NX> 105 server_nxnode_echo: NX> 1006 Session status: running
bye
Bye
NX> 999 Bye
Info: Closing connection to slave with pid 9990.
nxnode_reader: 1001 Bye.
1001 Bye.
nxnode_reader: NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/ldxxxxxxx/.nx/F-C-BG-NMS01-2046-E549076C3016E9B8407C21660EF0A2E4/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/ldxxxxxxx/.nx/F-C-BG-NMS01-2046-E549076C3016E9B8407C21660EF0A2E4/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
nxnode_reader: NX> 1006 Session status: closed
NX> 1006 Session status: closed
server_nxnode_echo: NX> 596 Session startup failed.
NX> 596 Session startup failed.
server_nxnode_echo: NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/ldxxxxxxx/.nx/F-C-BG-NMS01-2046-E549076C3016E9B8407C21660EF0A2E4/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
session_close E549076C3016E9B8407C21660EF0A2E4
server_nxnode_echo: NX> 1006 Session status: closed



FILE:/home/ldxxxxxxx/.nx/F-C-BG-NMS01-2046-E549076C3016E9B8407C21660EF0A2E4/session

NXAGENT - Version 3.4.0

Copyright (C) 2001, 2010 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '10916'.
Session: Starting session at 'Sat Jan 22 10:38:08 2011'.
Info: Proxy running in server mode with pid '10916'.
Info: Waiting for connection from '127.0.0.1' on port '6046'.
Info: Accepted connection from '127.0.0.1'.
Warning: Connected to remote version 3.3.0 with local version 3.4.0.
Info: Connection with remote proxy completed.
Info: Using MODEM link parameters 256/24/1/0.
Info: Using agent parameters 5000/50/50/0/0.
Info: Using cache parameters 4/4096KB/4096KB/4096KB.
Info: Using pack method 'adaptive-3' with session 'gnome'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 9/9.
Info: No suitable cache file found.
Info: Listening to X11 connections on display ':2046'.
Info: Established X client connection.
Info: Using shared memory parameters 1/1/1/1024K.
Info: Using alpha channel in render extension.
Info: Using local device configuration changes.
InitOutput: Locale en_US.UTF-8 not supported by X
InitOutput: cannot set locale modifiers.
Error: Aborting session with 'Could not open default font 'fixed''.
Session: Aborting session at 'Sat Jan 22 10:39:09 2011'.
Session: Session aborted at 'Sat Jan 22 10:39:09 2011'.
Warning: Signals were not blocked in process with pid '10916'.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.



NXClient Session Log:

NXPROXY - Version 3.3.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '4971'.
Session: Starting session at 'Sat Jan 22 10:38:20 2011'.
Warning: Connected to remote version 3.4.0 with local version 3.3.0.
Warning: Consider checking [http://www.nomachine.com/](http://www.nomachine.com/) for updates.
Info: Connection with remote proxy completed.
Info: Using MODEM link parameters 256/24/1/0.
Info: Using cache parameters 4/4096KB/4096KB/4096KB.
Info: Using pack method 'adaptive-3' with session 'gnome'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 9/9.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '12046'.
Session: Session started at 'Sat Jan 22 10:38:21 2011'.
Info: Established X server connection.
Info: Using shared memory parameters 1/1024K.
Session: Terminating session at 'Sat Jan 22 10:39:21 2011'.

---

