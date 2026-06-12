---
title: "boot problem"
date: 2009-10-31
forum: General Help
---

### Post by Friedhay on 2009-10-31
I have been trying to get the most out of my ati video card and when i installed a new ati driver and restarted it, i noticed that just as the video screen kicked in the screen went dark.  it appears that the system is working but i cant see it.  i have a wubi install and the boot sector of windows is corrupted but i haven't taken the time to restore it because i use mostly ubuntu 9.04.  i have a second drive that is formatted windows xp boot and it has taken over the primary boot functions but they are limited. i can reach all files on the corrupted drive from that drive and until i messed up ubuntu i could work with all files in the system.  i tried using my live disk to go in and work on the ubuntu problem, but i cant access ubuntu from the live disk

what do i do?

---

### Post by morphodone on 2009-10-31
You need to get logged into a terminal.

'Ctrl + Alt + F1'

Then issue the following command:

```
dpkg-reconfigure xserver-xorg
```

---

