---
title: "lost my  D: drive after virus attack"
date: 2009-11-29
forum: General Help
---

### Post by phil.hermetic@langtoft.ne on 2009-11-29
Hi All,
 I have been using jaunty on a dual hard drive pc and all worked very well untill my windows (XP pro) HDD got a bad case of win32 vitro virus. now I have rebuilt it and am back online, I find that the "select operating system to boot" dialogue doesnt appear during the boot sequence, and my D:(containing the jaunty O/S) drive does not appear in "my computer" although it is in device manager, and it says "this device is working properly". I have tried to assign a drive letter, but the option is greyed out in "computer management" Any suggestions?
phil.

---

### Post by sensay on 2009-11-29
Hi, reinstalling windows will cause the GRUB bootloader to be overwritten thus you wont see any dual booting options, windows will just load on its own. If you boot a live CD you can reinstall GRUB and that should be that.

See Here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You shouldnt be using windows to mess around like this either. Windows wont see your ubuntu partition because its in a format that windows cant read. Did you ever see the ubuntu partition under windows? Why are you trying to assign drive letters and silly things like this. Uninformed tinkering rarely helps anything.

---

### Post by ugm6hr on 2009-11-29
Also, you generally can't "see" a Linux partition from Windows, since it is ext3/4.

---

### Post by phil.hermetic@langtoft.ne on 2009-11-29
Thanks for that chaps,

Windows can see the partition under disc management, what confused me was that the D: drive does not appera in "my computer", which it did right up to the virus attack. I will boot from the ubuntu disk and see if grub returns. 
TY!
Phil

---

### Post by sensay on 2009-11-29
> **phil.hermetic@langtoft.ne said:**
> Thanks for that chaps,

Windows can see the partition under disc management, what confused me was that the D: drive does not appera in "my computer", which it did right up to the virus attack. I will boot from the ubuntu disk and see if grub returns. 
TY!
Phil

You'll have to enter a few console commands to get grub back up and running, all is explained in the link i gave.

---

