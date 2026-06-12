---
title: "megaglest (game) crashes on startup, screenresizes, then game aborts"
date: 2012-01-07
forum: General Help
---

### Post by andrewcd on 2012-01-07
Hi All,  I'm having an issue with the game Megaglest, would appreciate help.  When I type it into a terminal, I get the following output.  Seems like its some problem with the rendering?  My screen resolution gets altered, then the program aborts.

```
v3.6.0-GNUC: 40403 [64bit]-Dec 11 2011 13:45:55, SVN: [$Rev: 2954 $], [STREFLOP]
megaglest.real: brw_wm_surface_state.c:625: brw_update_renderbuffer_surface: Assertion `((((brw)->intel.intelScreen->deviceID == 0x2E02 || (brw)->intel.intelScreen->deviceID == 0x2E12 || (brw)->intel.intelScreen->deviceID == 0x2E22 || (brw)->intel.intelScreen->deviceID == 0x2E32 || (brw)->intel.intelScreen->deviceID == 0x2E42) || ((brw)->intel.intelScreen->deviceID == 0x2A42))) || (tile_x == 0 && tile_y == 0)' failed.
```

---

### Post by dino99 on 2012-01-07
how have you installed it ?

[http://glest.org/glest_board/index.php?topic=5751.0](http://glest.org/glest_board/index.php?topic=5751.0)

---

### Post by andrewcd on 2012-01-07
I had thought so, but I went ahead and double-checked:

```
andrew@andrew-laptop:~$ echo 'deb http://archive.getdeb.net/ubuntu lucid-getdeb games' | sudo tee -a /etc/apt/sources.list && wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
[sudo] password for andrew: 
deb http://archive.getdeb.net/ubuntu lucid-getdeb games
OK
andrew@andrew-laptop:~$ sudo apt-get megaglest
E: Invalid operation megaglest
andrew@andrew-laptop:~$ sudo apt-get install megaglest
Reading package lists... Done
Building dependency tree       
Reading state information... Done
megaglest is already the newest version.
The following packages were automatically installed and are no longer required:
  libgdal1-1.6.0 linux-headers-2.6.32-33 acroread-common libspatialite2
  libgeos-3.1.0 libqgis1.7.1 linux-headers-2.6.32-33-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
andrew@andrew-laptop:~$ megaglest
v3.6.0-GNUC: 40403 [64bit]-Dec 11 2011 13:45:55, SVN: [$Rev: 2954 $], [STREFLOP]
megaglest.real: brw_wm_surface_state.c:625: brw_update_renderbuffer_surface: Assertion `((((brw)->intel.intelScreen->deviceID == 0x2E02 || (brw)->intel.intelScreen->deviceID == 0x2E12 || (brw)->intel.intelScreen->deviceID == 0x2E22 || (brw)->intel.intelScreen->deviceID == 0x2E32 || (brw)->intel.intelScreen->deviceID == 0x2E42) || ((brw)->intel.intelScreen->deviceID == 0x2A42))) || (tile_x == 0 && tile_y == 0)' failed.
Aborted
andrew@andrew-laptop:~$
```

it is in fact installed.  it just crashes on start because of something to do with the screen or the resolution or something.

---

