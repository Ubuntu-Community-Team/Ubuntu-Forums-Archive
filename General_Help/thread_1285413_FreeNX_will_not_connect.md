---
title: "FreeNX will not connect"
date: 2009-10-07
forum: General Help
---

### Post by madmaze on 2009-10-07
Hello there,
I have an 9.04 ubuntu machine onto which i installed freenx and have been trying to get it to work for a few days now.

As far as I can tell it is properly installed and working,
but then when I try to connect from my XP laptop I get the following errors:

NX> 203 NXSSH running with pid: 3644
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: x.x.x.x on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: madmaze
NX> 102 Password:
NX> 103 Welcome to: madmaze-desktop user: madmaze
NX> 105 listsession --user="madmaze" --status="suspended,running" --geometry="1680x1050x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'madmaze'

Server     Display Username        Remote IP       Session ID
------ ------- --------------- --------------- --------------------------------
NX> 105 startsession  --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="osiris" --type="unix-gnome" --geometry="1674x988" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1674x988x32+render"

/usr/bin/nxserver: line 458: /var/lib/nxserver/db/running/sessionId{0B31677ED12921BFE97D9871DC654E9D}: Permission denied
/usr/bin/nxserver: line 222: /var/lib/nxserver/db/running/sessionId{}: No such file or directory
NX> 280 Exiting on signal: 15

Im not sure if its trying to restart a session or something, but there is nothing in /var/lib/nxserver/db/running/

has anyone run into this problem?

PS: I have another ubuntu 9.04 machine, but thats running the server edition, shouldnt make a diff right, but that one worked without a hitch..

---

