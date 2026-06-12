---
title: "nxserver 596 Session startup failed."
date: 2011-05-06
forum: General Help
---

### Post by berryboy on 2011-05-06
hello,

as u can tell from my title im unable to connect via nxclient to my remote desktop when i try i get this in the log 

```
Can't open /var/lib/nxserver/db/running/sessionId{F83992670669DE66AABE321BB44AD3E5}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{F83992670669DE66AABE321BB44AD3E5}': No such file or directory
```

the hard drive is not full and i have tried restarting nxserver through putty + hard boot

some pointers would be great :)

---

### Post by berryboy on 2011-05-07
think i have narrowed it down.

if i reboot the server i can use nxserver no probs, however if i log in as another user before i start nxserver and start my trackmania dedicated server, then try to start nx it fails,

so the conflict is with 'TrackmaniaServer' and nxserver o_0
both running on different accounts (same GID)

the trackmania server uses ports : 
game coms: 2350
p2p coms: 3450
xmlrpc (remote control): 5000

nxserver port: 22?

when nxserver is running, TrackmaniaServer starts with no errors
```
Starting TmForever v2011-02-21...
Initializing...
Configuration file : C:\home\TM\TMUF\GameData\Config\dedicated_cfg.txt
Loading system configuration...
...system configuration loaded
Loading cache...
...OK
Listening for xml-rpc commands on port 5001.

```

but as u can see xml-rpc is listening on port 5001 instead of 5000, also the game server is not running or atleast i cant join it :/

i really need a little nudge just something to go on!

thanks in advance :)

---

