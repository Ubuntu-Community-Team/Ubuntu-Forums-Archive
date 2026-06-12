---
title: "freeNX (almost got it working!)"
date: 2010-12-29
forum: General Help
---

### Post by tmilam on 2010-12-29
FreeNX and I have been battling each other all morning. I think I'm winning....hats off to anyone who tries to get freeNX working on 10.10! Here is my log, can you see what the problem is?

```

NX> 203 NXSSH running with pid: 3256
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.10 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
Linux labserver 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: tyler
NX> 102 Password: 
NX> 103 Welcome to: labserver user: tyler
NX> 105 listsession --user="tyler" --status="suspended,running" --geometry="1366x768x32+render+fullscreen" --type="unix-default"
NX> 127 Sessions list of user 'tyler' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: tyler
NX> 105 startsession  --rootless="1" --virtualdesktop="0" --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Ubuntu" --type="unix-default" --client="winnt" --kbload="pc105/en_US" --keymap="en_US" --keyboard="pc105/en_US" --aux="1" --screeninfo="1366x768x32+render+fullscreen" 

Could not find ':' in DISPLAY: 

(ssh-askpass:8451): Gtk-WARNING **: cannot open display: localhost:10.0
Permission denied (publickey,password).
NX> 280 Exiting on signal: 15

```

It seems to be a problem with the X server, but what I'm not sure.

---

### Post by tmilam on 2010-12-29
I've decided to use NoMachine's free NX server and client from [http://www.nomachine.com](http://www.nomachine.com)

It worked immediately, so I'm going to stick with that :D

---

