---
title: "Grub 1.99 won't save defualt OS with startupmanager"
date: 2011-04-30
forum: General Help
---

### Post by SkylinesSuck on 2011-04-30
Okay, so I upgraded my wife's dual boot netbook (Ubuntu/Win7) from 10.10 to 11.4.  Windows was set as the default OS in Grub v 1.98 via startupmanager in 10.10 and that's the way I want it to be again.  

After the 11.4 upgrade, Ubuntu 11.4 is set to defualt and even though I changed the default in startupmanager it always defaults to Ubuntu on boot.  It's interesting to note that when I go back in to startupmanager to see what's up after reboot, it still has Win 7 selected.  Also, the choices in startupmanager look a little different from what shows up in grub.  Grub shows just the latest version of ubuntu (and recovery mode), the memtest stuff, windows, and "previous versions of ubuntu" while startupmanger just lists all three ubuntu version w/recovery options, memtest stuff, and Win 7.  If I do sudo update-grub in terminal, it lists the available options just like startupmanager does.

Bottom line, Win 7 will boot if manually selected, but I can't set it to default, and this is my wife's netbook so she wants it put back :(


**One other thing I just remembered and I don't know if it would matter or not.  I did the original Ubuntu install first, then win 7.  I used a windows program called easyBCD to get back the ability to choose which OS on startup.  When I upgraded 10.10 to 11.4, Grub is back in charge.  If I manually select Win7 to boot in grub, that easyBCD selection menu will pop up for a sec, offereing windows or ubuntu.  Could this be confusing startupmanager and not letting my changes take effect?

---

### Post by wilee-nilee on 2011-04-30
drs305 has a thread on the newest grub 1.99, can't find it but this one should give you the answer, and you can look for the other, I believe it is mentioned that startup manager isn't up to date with natty.
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

Found the other thread in the one above.
[http://ubuntuforums.org/showthread.php?p=10720316#post10720316](http://ubuntuforums.org/showthread.php?p=10720316#post10720316)

---

