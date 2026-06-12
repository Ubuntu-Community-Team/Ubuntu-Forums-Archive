---
title: "FreeNX shadow session"
date: 2012-04-18
forum: General Help
---

### Post by platinummonkey on 2012-04-18
I have FreeNX server installed and users can log in just fine. The problem arises when users would like to shadow a session. It plain and simple does not work, although the user who's session is requesting to be shadowed is presented with the confirmation dialog (so that's a start), but fails right after confirmation.
Using the NoMachine version is not an option as we will need more than the maximum allowed.

I have verified that the changing AGENT_EXTRA_OPTIONS with and without "-nolisten tcp" has no effect. The users have a limit of 5 sessions (so 1 user + 1 shadow doesn't breach this limit) and the overall session limit is sufficiently high for our purposes (for now these are the only two sessions).

If anybody has any additional information to resolve this issue, it would be greatly appreciated.

The server config:
```
cat /etc/nxserver/node.conf | grep -ve '^#' | grep -ve '^$'
SSHD_PORT=1209
DISPLAY_BASE=1001
SESSION_LIMIT=25
SESSION_USER_LIMIT=5
DISPLAY_LIMIT=25
ENABLE_PERSISTENT_SESSION="all"
ENABLE_MIRROR_VIA_VNC=1
ENABLE_DESKTOP_SHARING=1
ENABLE_SESSION_SHADOWING_AUTHORIZATION=1
ENABLE_INTERACTIVE_SESSION_SHADOWING=1
NX_LOG_LEVEL=7
NX_LOGFILE=/var/log/nxserver.log
SESSION_LOG_CLEAN=0
```

The nxserver.log as the user trying to shadow attempts: (master user: "xxxx", shadowing user: "yyyy", on host: "host")
```
cat /var/log/nxserver.log
-- NX SERVER START:  - ORIG_COMMAND=
-- NX SERVER START:  - ORIG_COMMAND=
Info: Using fds #4 and #3 for communication with nxnode.
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: yyyy
NX> 102 Password:
Info: Auth method: ssh yyyy@127.0.0.1's password:
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 716 Slave mode started successfully.
nxnode_reader: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
nxnode_reader: NX> 716 finished
nxnode_reader: NX> 1001 Bye.

NX> 103 Welcome to: host user: yyyy
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
1001    unix-gnome       5B35808234323A4D8277F794527BFC3E --D--PSA    24 1914x1012      Running     host (xxxx) (Shadowed)
0       Local            639B671210FCE02100D4A90C44850D86 --------                      Running     X0 (Local)
0       Local            98F246415D9EA65BC926E0CA1E8DBC74 --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 listsession --type="shadow"
NX> 105 attachsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="hostshadow" --type="shadow" --client="winnt" --keyboard="pc102/en_US" --id="5B35808234323A4D8277F794527BFC3E" --display="1001" --geometry="1914x1012" --resize="1"

NX> 726 Asking user for authorization to attach to session
Info: Using /etc/nxserver/nxacl to change session parameters or deny session.
&link=adsl&backingstore=1&encryption=1&cache=16M&images=64M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=hostshadow&type=shadow&client=winnt&keyboard=pc102/en_US&id=5B35808234323A4D8277F794527BFC3E&display=1001&geometry=1914x1012&resize=1&clientproto=3.2.0&login_method=SSH&shadowdisplay=1001&shadowhost=&shadowcookie=******&shadowuser=xxxx&user=yyyy&userip=140.239.209.66&uniqueid=858B82DD3410A5FA08EE35153B0FD7F6&display=1003&host=127.0.0.1
nxnode_reader: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
server_nxnode_echo: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
nxnode_reader: NX> 700 Session id: host-1001-858B82DD3410A5FA08EE35153B0FD7F6
NX> 700 Session id: host-1001-858B82DD3410A5FA08EE35153B0FD7F6
nxnode_reader: NX> 705 Session display: 1001
nxnode_reader: NX> 703 Session type: shadow
server_nxnode_echo: NX> 700 Session id: host-1001-858B82DD3410A5FA08EE35153B0FD7F6
nxnode_reader: NX> 701 Proxy cookie: 3def610d9e80da114ce1f978fa4d5a2c
nxnode_reader: NX> 702 Proxy IP: xyz.xyz.xyz.xyz
nxnode_reader: NX> 706 Agent cookie: 3def610d9e80da114ce1f978fa4d5a2c
nxnode_reader: NX> 704 Session cache: shadow
nxnode_reader: NX> 707 SSL tunneling: 1
nxnode_reader: Disk quotas for user yyyy (uid 1000): none
nxnode_reader: NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/yyyy/.nx/F-C-host-1001-858B82DD3410A5FA08EE35153B0FD7F6/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 705 Session display: 1001
NX> 703 Session type: shadow
NX> 701 Proxy cookie: 3def610d9e80da114ce1f978fa4d5a2c
NX> 702 Proxy IP: xyz.xyz.xyz.xyz
NX> 706 Agent cookie: 3def610d9e80da114ce1f978fa4d5a2c
NX> 704 Session cache: shadow
NX> 707 SSL tunneling: 1
Disk quotas for user yyyy (uid 1000): none
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/yyyy/.nx/F-C-host-1001-858B82DD3410A5FA08EE35153B0FD7F6/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
server_nxnode_echo: NX> 705 Session display: 1001
nxnode_reader: Error: Aborting session with 'Server is already active for display 1001
nxnode_reader: If this server is no longer running, remove /tmp/.X1001-lock
nxnode_reader: and start again'.
nxnode_reader: Session: Aborting session at 'Wed Apr 18 11:19:32 2012'.
nxnode_reader: Session: Session aborted at 'Wed Apr 18 11:19:32 2012'.
nxnode_reader: NX> 1006 Session status: closed
Error: Aborting session with 'Server is already active for display 1001
If this server is no longer running, remove /tmp/.X1001-lock
and start again'.
Session: Aborting session at 'Wed Apr 18 11:19:32 2012'.
Session: Session aborted at 'Wed Apr 18 11:19:32 2012'.
NX> 1006 Session status: closed
server_nxnode_echo: NX> 703 Session type: shadow
server_nxnode_echo: NX> 701 Proxy cookie: 3def610d9e80da114ce1f978fa4d5a2c
server_nxnode_echo: NX> 702 Proxy IP: xyz.xyz.xyz.xyz
server_nxnode_echo: NX> 706 Agent cookie: 3def610d9e80da114ce1f978fa4d5a2c
nxnode_reader: rm: cannot remove `/tmp/.X1001-lock': Operation not permitted
nxnode_reader: rm: cannot remove `/tmp/.X11-unix/X1001': Operation not permitted
rm: cannot remove `/tmp/.X1001-lock': Operation not permitted
rm: cannot remove `/tmp/.X11-unix/X1001': Operation not permitted
server_nxnode_echo: NX> 704 Session cache: shadow
server_nxnode_echo: NX> 707 SSL tunneling: 1
NX> 105 server_nxnode_echo: NX> 596 Session startup failed.
NX> 596 Session startup failed.
server_nxnode_echo: NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/yyyy/.nx/F-C-host-1001-858B82DD3410A5FA08EE35153B0FD7F6/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
session_close 858B82DD3410A5FA08EE35153B0FD7F6
nxnode_reader: rm: cannot remove `/tmp/.X1001-lock': Operation not permitted
rm: cannot remove `/tmp/.X1001-lock': Operation not permitted
server_nxnode_echo: NX> 1006 Session status: closed
nxnode_reader: rm: cannot remove `/tmp/.X11-unix/X1001': Operation not permitted
rm: cannot remove `/tmp/.X11-unix/X1001': Operation not permitted
Info: Closing connection to slave with pid 5123.
nxnode_reader: 1001 Bye.
1001 Bye.
nxnode_reader: NX> 1001 Bye.
NX> 1001 Bye.
server_nxnode_echo: NX> 1001 Bye.
Info: Closing connection to slave with pid 3289.
```

---

### Post by platinummonkey on 2012-04-26
bump.

I have yet to find anyone with this working for 10.04 and newer...

---

### Post by derpishi on 2012-05-09
> **platinummonkey said:**
> bump.

I have yet to find anyone with this working for 10.04 and newer...

has this been resolved. here is my nxserver.log. any suggestions?
```
mvyvoda@Vyvoda-Laptock:/var/log$ cat nxserver.log 
-- NX SERVER START: -c /usr/NX/bin/nxserver - ORIG_COMMAND=
-- NX SERVER START:  - ORIG_COMMAND=
Info: Using fds #4 and #3 for communication with nxnode.
HELLO NXSERVER - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: mvyvoda
NX> 102 Password: 
Info: Auth method: passdb userdb check

NX> 103 Welcome to: Vyvoda-Laptock user: mvyvoda
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            BD5CFA0246E76471D987A43FADB9A8D8 --------                      Running     X0 (Local)
0       Local            4C244FBD3932538F2332D7A7F939D3DC --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            246E74ABF1CFBFA363D4B6B3E5AAE322 --------                      Running     X0 (Local)
0       Local            7D0991439A93CEBF76211CF8F05F9591 --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 attachsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Vyvoda-Laptock" --type="shadow" --client="winnt" --keyboard="pc102/en_US" --id="7D0991439A93CEBF76211CF8F05F9591" --display="0"

&link=lan&backingstore=1&encryption=1&cache=16M&images=64M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=Vyvoda-Laptock&type=shadow&client=winnt&keyboard=pc102/en_US&id=7D0991439A93CEBF76211CF8F05F9591&display=0&clientproto=3.2.0&shadowdisplay=0&shadowhost=&shadowcookie=******&user=mvyvoda&userip=192.168.11.18&uniqueid=ED31F84FEEFB3EB82104DA972051367A&display=1000&host=127.0.0.1 
NX> 1000 NXNODE - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
server_nxnode_echo: NX> 1000 NXNODE - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 700 Session id: Vyvoda-Laptock-1000-ED31F84FEEFB3EB82104DA972051367A
NX> 705 Session display: 1000
NX> 703 Session type: shadow
NX> 701 Proxy cookie: 0fe47db0dafefdb649019d4d3a5a5a3b
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 0fe47db0dafefdb649019d4d3a5a5a3b
NX> 704 Session cache: shadow
NX> 707 SSL tunneling: 1
server_nxnode_echo: NX> 700 Session id: Vyvoda-Laptock-1000-ED31F84FEEFB3EB82104DA972051367A
server_nxnode_echo: NX> 705 Session display: 1000
server_nxnode_echo: NX> 703 Session type: shadow
server_nxnode_echo: NX> 701 Proxy cookie: 0fe47db0dafefdb649019d4d3a5a5a3b
server_nxnode_echo: NX> 702 Proxy IP: 127.0.0.1
server_nxnode_echo: NX> 706 Agent cookie: 0fe47db0dafefdb649019d4d3a5a5a3b
server_nxnode_echo: NX> 704 Session cache: shadow
server_nxnode_echo: NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
server_nxnode_echo: NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
server_nxnode_echo: NX> 710 Session status: running
server_nxnode_echo: NX> 1002 Commit
session_status ED31F84FEEFB3EB82104DA972051367A Running
NX> 105 server_nxnode_echo: NX> 1006 Session status: running
bye
Bye
NX> 999 Bye
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/mvyvoda/.nx/F-C-Vyvoda-Laptock-1000-ED31F84FEEFB3EB82104DA972051367A/session". You might also want to try: ssh -X myserver; /usr/NX/bin/nxnode --agent to test the basic functionality. Session log follows:
NX> 1006 Session status: closed
server_nxnode_echo: NX> 596 Session startup failed.

```

---

### Post by platinummonkey on 2012-05-09
nope not yet :(

---

### Post by derpishi on 2012-05-11
> **platinummonkey said:**
> nope not yet :(

How did you get unix-gnome to show up in your display name? I only have Local. I think that might be my problem...

---

### Post by platinummonkey on 2012-05-12
> **derpishi said:**
> How did you get unix-gnome to show up in your display name? I only have Local. I think that might be my problem...

Unix-gnome is a freenx session. Local is the actual local display for the person sitting in front of the machine. That isn't supported yet by freenx I believe and is a different issue entirely from mine.

---

### Post by wgregori on 2013-02-21
Apparently this is a known bug.  I got around it by installing the nomachine version.  Go to [http://nomachine.com](http://nomachine.com) and follow the instrucutions to install the client, node and server.  They all need to be installed since there are common libs that they need.  I then used the nomachine client on my remote machine to capture the shadow session.  it works very well.

Wayne

---

### Post by platinummonkey on 2013-02-21
This thread is very old. Also please reread my original post as to why nomachine is not a viable option.

Unless you are suggesting running a freenx server and all clients use nomachine clients. This works *sometimes* but varies from experience to experience.

---

