---
title: "FRee NX Server stopped working after upgrade to Karmic"
date: 2009-11-10
forum: General Help
---

### Post by psypher on 2009-11-10
HI All,

I have successfully upgraded from Intrepid to Jaunty to karmic. Only issue seems to be with Free NX Server. I have un-installed completely and re-installed with instructions found at: [http://ubuntuguide.org/wiki/Ubuntu:Karmic#FreeNX]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#FreeNX") 

But when I try connect from a Freen NX running on a jaunty PC i get the following error:

```
NX> 203 NXSSH running with pid: 21503
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: IP OF SERVER on port: 22
NX> 202 Authenticating user: nx
This computer system is for authorized users only. All activity is logged and regulary checked by systems personal. Individuals using this system without authority or in excess of their authority are subject to having all their services revoked. Any illegal services run by user or attempts to take down this server or its services will be reported to local law enforcement, and said user will be punished to the full extent of the law. Anyone using this system consents to these terms.
NX> 208 Using auth method: publickey
/usr/bin/X11/xauth:  timeout in locking authority file /var/lib/nxserver/home//.Xauthority
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: USERNAME
NX> 102 Password: 
NX> 103 Welcome to: HOSTNAME OF CLIENT user: USERNAME
NX> 105 listsession --user="USERNAME" --status="suspended,running" --geometry="1920x1200x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'USERNAME' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: USERNAME
NX> 105 startsession  --link="modem" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="HOSTNAME OF SERVER" --type="unix-gnome" --geometry="1920x1151" --client="linux" --keyboard="pc105/us" --screeninfo="1920x1151x24+render" 

/usr/bin/nxserver: line 448: /var/lib/nxserver/db/running/sessionId{F15E882317BB5A51FE21ED8E53717511}: Permission denied
NX> 280 Exiting on signal: 15


```


I have looked up this error and cannot find anything related to it.

Thanks

---

