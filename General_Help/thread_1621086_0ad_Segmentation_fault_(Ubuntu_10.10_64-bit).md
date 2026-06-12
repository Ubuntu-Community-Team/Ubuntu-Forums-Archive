---
title: "0ad Segmentation fault (Ubuntu 10.10 64-bit)"
date: 2010-11-13
forum: General Help
---

### Post by gypsumwolf on 2010-11-13
This is what happens. I am using the newest graphics driver from Nvidia, not the one that Jockey installs. Any ideas?

VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

```

:~$ 0ad
TIMER| InitVfs: 324.531 ms
TIMER| InitScripting: 54.3108 ms
TIMER| CONFIG_Init: 23.7979 ms
TIMER| write_sys_info: 795.243 us
TIMER| InitRenderer: 276.253 ms
TIMER| ps_console: 1.91032 ms
TIMER| ps_lang_hotkeys: 21.8842 ms
TIMER| common/setup.xml: 1.33886 ms
TIMER| common/styles.xml: 636.608 us
TIMER| common/sprite1.xml: 2.27736 ms
TIMER| common/init.xml: 32.0218 ms
TIMER| pregame/sprites.xml: 1.36646 ms
TIMER| pregame/styles.xml: 11.5483 ms
TIMER| pregame/mainmenu.xml: 20.986 ms
TIMER| common/global.xml: 927.025 us
SND| alc_init: success, using ALSA Software
Segmentation fault
:~$ 
```

---

### Post by Slammy on 2010-11-14
Newest Newest ? As in released 2 days ago (260.19.21 ) ?
These ( and only these ) solved the unsavory SegFault. Prior to that, you had to downgrade your NVidia drivers to 259.something.

Go to this thread on the WildFire Forum : [http://www.wildfiregames.com/forum/index.php?showtopic=13668](http://www.wildfiregames.com/forum/index.php?showtopic=13668)

---

### Post by gypsumwolf on 2010-11-15
It was probably a week ago.

I will try this one and see what happens:

> Version:
260.19.21 Certified

Release Date:
2010.11.11

Operating System:
Linux 64-bit

Language:
English (U.S.)

File Size:
45.7 MB 

---

### Post by gypsumwolf on 2010-11-16
I tried it and when I click on single player it freezes and I have to kill gdm because pkill 0ad does not work.

---

