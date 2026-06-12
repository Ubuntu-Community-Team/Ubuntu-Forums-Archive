---
title: "FreeNX server failing to create X session"
date: 2006-02-19
forum: General Help
---

### Post by whizzoman on 2006-02-19
Hi!

I'm running FreeNX Server Version 1.4.0-45-SVN OS (GPL) from [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl)

With help from the HOWTO ([http://ubuntuforums.org/showthread.php?t=97277](http://ubuntuforums.org/showthread.php?t=97277)) and the FreeNX FAQ/Server at [http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Server](http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Server) I have managed to get a Windows Client 1.5.0-138 and the local client 1.5.0-135 to login.

They both show a black screen with a cursor but no screen background color and no menus. I have tried different display resolutions without any luck.

NX Session Manager server session log (see below) shows errors trying to get X started: "_IceTransTransNoListen: unable to find transport: tcp" etc.

I have tried two possible solutions for this. Deleting the file and reconfiguring X without any luck.

Interactive login through the attached keyboard and mouse works fine.

Where should I look now, please?

Regards,
Erik

Please find log files below.


nxserver.log:

-- NX SERVER START: -c /usr/lib/nx/nxserver
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: xxxx
NX> 102 Password:
Info: Auth method: passdb
NX> 103 Welcome to: ubuntu user: xxxx
NX> 105 listsession --user="xxxx" --status="suspended,running" --geometry="1152x864x32+render" --type="unix-gnome"
NX> 127 Sessions list of user xxxx' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: xxxx
NX> 105 startsession --session="ubuntu" --type="unix-gnome" --cache="8M" --images="32M" --cookie="******" --link="lan" --kbtype="pc102/dk" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="fullscreen" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1152x834x32+render"

&session=ubuntu&type=unix-gnome&cache=8M&images=32M&cookie=******&link=lan&kbtype=pc102/dk&nodelay=1&encryption=1&backingstore=when_requested&geometry=fullscreen&media=0&agent_server=&agent_user=&agent_password=******&screeninfo=1152x834x32+render&clientproto=1.5.0&user=xxxx&userip=192.168.0.8&uniqueid=0145B8EE566B0A298F510F6CA6C1F823&display=1000
NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: ubuntu-1000-0145B8EE566B0A298F510F6CA6C1F823
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 5aab2b30d0c23b999759e0ee93373713
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 5aab2b30d0c23b999759e0ee93373713
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye


NX Session Manager Server log:

Info: Agent running with pid '10412'.
nxagentProcessOptionsFile: Option file is [/home/xxxx/.nx/C-ubuntu-1000-B75CD82EAD3DAE731155A7BDA954E0D4/options].
nxagentProcessOptionsFile: Option file is 197 bytes long.
nxagentParseOptionString: Warning ignored option 'cache' = '8M'.
nxagentParseOptionString: Warning ignored option 'images' = '32M'.
nxagentParseOptionString: Warning ignored option 'link' = 'lan'.
nxagentParseOptionString: Warning ignored option 'type' = 'unix-gnome'.
nxagentParseOptionString: Warning ignored option 'cleanup' = '0'.
nxagentParseOptionString: Warning ignored option 'accept' = '127.0.0.1'.
nxagentParseOptionString: Warning ignored option 'cookie' = 'ee7dfee85006ce85827abdd9c642e413'.
nxagentParseOptionString: Warning ignored option 'samba' = '0'.
nxagentParseOptionString: Warning ignored option 'media' = '0'.
Info: Proxy running in server mode with pid '10412'.
Info: Waiting for connection from '127.0.0.1' on port '5000'.
Info: Accepted connection from '127.0.0.1' on port '34382'.
Info: Connection with remote proxy established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/8/0/0.
Info: Using agent parameters 98304/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using processor load limit.
Info: Not using persistent cache.
Info: Starting X protocol compression.
Info: Established X client connection.
Info: Using shared memory support in X server.
Info: Using fast copy area mode in agent.
Info: Using fast get image mode in agent.
Info: Using render cleanup parameters 8/20/23/24/25/26.
Info: Using local render version 0.8 with remote version 0.10.
Info: Using image cleanup parameters 0/0/0/0.
Info: Detected window manager.
Info: Not using local device configuration changes.
Info: Using alpha channel in render extension.
Info: Adding the X connection 3 to the device set.
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Info: Session started, state is [SESSION_UP].
Info: Entering dispatch loop with exception 0x0.
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/ubuntu:/tmp/.ICE-unix/10426


NX Session Manager client log:

Info: Proxy running in client mode with pid '9140'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/8/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using persistent cache.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

---

