---
title: "Install linux without live image question"
date: 2011-01-06
forum: General Help
---

### Post by sshields on 2011-01-06
Probably easy for someone, but I'm stumped.


  Here's the issue: Old Sony Viao pcg-vx89. These are notorious for the fact that the bios will  not allow any booting of cdroms or usb. Period. It's a broken bios. The  bios update tool that Sony provides requires you to boot from usb  floppy, which doesn't work, so catch 22. Can't USB key boot either. Hard  drive or nothing.


  I have WindowsXP on Partition 0 of the disk and it boots fine. I'd  like to either dual boot or blow XP away and completely go with Xubuntu  (256mb +P3 so ya).


  My question is, how do you install Linux from the XP partition into  the other partion without using the live cd/usb? Every install how to  I've seen assumes you are installing from a reboot into live cd/usb.


  I can autoplay any linux CD from XP but not enough ram for Wubi if  that would even help me, and the "full install or demo" option requires  me to reboot into the CD which is hard broken because of the lame BIOS.

(Probably going to be Xubuntu or Crunchbang if that matters.)


  Any help **appreciated**!! Thank you.- S

---

### Post by Harrycrossxx on 2011-01-06
try Wubi, it installs ubuntu from windows and makes a dual boot menu on startup. 

[http://wubi.sourceforge.net/](http://wubi.sourceforge.net/)

---

### Post by babybean on 2011-01-06
Tricky :p
The way I see it (and I may be completely wrong) is that you really have 2 choices. 1 is to install it over a network, if the bios supports that. The other way would be to install it onto the hard drive from another machine, then replace the disk. Of course both have there disadvantages. Hopefully it gives you a few idears to start looking though.

Also check out
[http://ubuntuforums.org/showthread.php?t=714852](http://ubuntuforums.org/showthread.php?t=714852)

---

### Post by marin123 on 2011-01-06
its a good idea to install on another computer. and you can check out lubuntu, which seems to be lighter then xubuntu...

---

### Post by oldfred on 2011-01-06
Best choice is use another computer, if you can remove hard drive.

Does floppy work? Plop will let you boot USB from the floppy.
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

If you had a spare partition on drive you could install the ISO to that but if the boot loader did not work then you are out of luck.

---

### Post by sshields on 2011-01-06
Ah.. 

Looks like Wubi is my answer. I can install Wubi into the XP partition and then migrate the wubi install over apparently.. 

Now if I can just find a walk through on Wubi install migration to a second partition.

---

### Post by sshields on 2011-01-06
Thanks!

---

