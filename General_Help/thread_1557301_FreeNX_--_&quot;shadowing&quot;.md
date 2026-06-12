---
title: "FreeNX -- &quot;shadowing&quot;"
date: 2010-08-20
forum: General Help
---

### Post by Gurtz on 2010-08-20
Hi all,

I have been trying for the last two days to be able to remote-control an existing session using FreeNX, but with no success. I am able to open a NEW session with no problems, but when I set the FreeNX client configuration to "Shadow", I get a "Could not find shadowed session" error. On the server (in the /etc/nxserver/node.conf file) I have set the following values:

ENABLE_DESKTOP_SHARING=1
ENABLE_SESSION_SHADOWING_AUTORIZATION=1
ENABLE_INTERACTIVE_SESSION_SHADOWING=1

The results I get in the log on the client are shown below.

Any help would be greatly appreciated!

Thanks,
Gurtz
==========

NX> 203 NXSSH running with pid: 15843
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.xxx on port: xxxxx
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: xxxxxxxx
NX> 102 Password: 
NX> 103 Welcome to: xxxxxxxx-laptop user: xxxxxxxx
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            23A56A74956FF969690B2347832DDF0B --------                      Running     X0 (Local)
0       Local            F8762CB43F66061078653FF48D5E9A32 --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            A20F809D0E1982E058FEF65DBDA2872A --------                      Running     X0 (Local)
0       Local            4369D6E44C64F90D1E804E5A4C531B38 --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 attachsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="xxxxxxxxxxxxxxShadow" --type="shadow" --client="linux" --keyboard="pc105/us" --id="A20F809D0E1982E058FEF65DBDA2872A" --display="0"

NX> 596 Could not find shadowed session A20F809D0E1982E058FEF65DBDA2872A. Session failed.
NX> 596 Sharing: 
NX> 105 NX> 280 Exiting on signal: 15

---

### Post by yang on 2010-08-20
I'm also seeing this exact problem. Gurtz, if you need an immediate workaround you can consider VNC and proxying VNC via NX.

---

### Post by Gurtz on 2010-08-21
Thanks for the suggestion, yang!

Can you clarify what you mean by "proxying VNC via NX"?

Gurtz

---

### Post by ICANSEEYOU7687 on 2010-09-06
Did you ever solve this?  I got it working well, except cant shadow the already running session, can only run new sessions.

---

### Post by Gurtz on 2010-09-07
> **ICANSEEYOU7687 said:**
> Did you ever solve this?  I got it working well, except cant shadow the already running session, can only run new sessions.

Unfortunately, no :sad:

In the end I gave up and decided to tunnel VNC over SSH. Though it's probably not the fastest solution, it is working, and I'm happy with it. It was frustrating to have hit a "brick wall" with FreeNX, though.

Anyway, good luck to you. If you ever do solve it, please post an update.

Thanks,
Gurtz

---

