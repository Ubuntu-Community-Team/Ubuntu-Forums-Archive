---
title: "Warsow crashes on game loading. Ubuntu Intel 82G33/G31 Graphics."
date: 2010-08-03
forum: General Help
---

### Post by glazs on 2010-08-03
Menu working normally, game crashes on level loading:
```

]map wca1
Opening UDP/IP socket: *:44400
==== G_Init ====
------- Server Initialization -------
SpawnServer: wca1
-------------------------------------
Initalizing 'bomb' gametype
loading configs/server/gametypes/bomb.cfg
bomb.cfg executed 
* Initializing gametype scripts
* Initializing Game module syntax
* Loaded script section 'progs/shared/constants.as'
* Loaded script section 'progs/shared/files.as'
* Loaded script section 'progs/gametypes/generic/matchstates.as'
* Loaded script section 'progs/gametypes/generic/bots.as'
* Loaded script section 'progs/gametypes/generic/items.as'
* Loaded script section 'progs/gametypes/bomb/media.as'
* Loaded script section 'progs/gametypes/bomb/players.as'
* Loaded script section 'progs/gametypes/bomb/bomb.as'
* Loaded script section 'progs/gametypes/bomb/generic.as'
* Loaded script section 'progs/gametypes/bomb/indicators.as'
* Loaded script section 'progs/gametypes/bomb/main.as'
* Loaded script section 'progs/gametypes/legacy/quake1.as'
********************
ERROR: Received signal 11

********************
==== G_Shutdown ====
WARNING: Spawning entity before map entities have been spawned
Closing SDL audio device...
SDL audio device shut down.
Error: Received signal 11


```

```

lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

```

Tried with default driver on 10.04 and driver from ppa:ubuntu-x-swat/x-updates.
Using very-very low graphics profile.
Help! I wanna play on work ;)

---

### Post by 0x656b694d on 2011-03-05
Hey, any luck with this problem?

(got the same on ubuntu 10.10 x86_64, nvidia)

---

