---
title: "Lost Windows in Grub2 Menu on Ubuntu 12.04 Beta"
date: 2012-04-11
forum: General Help
---

### Post by dragin33 on 2012-04-11
I'm running the latest beta of Ubuntu 12.04.  I have an Intel Raid 1 on my system and Windows 7 was installed first.  When i first installed Ubuntu Windows 7 was available in the Grub2 list.  I was trying to edit the default value of the menu and somewhere along the way Windows completely disappeared from the list.  Can someone help me get it back?


Originally all I edited was /etc/default/grub and changed this:
from GRUB_DEFAULT=0 ---->  GRUB_DEFAULT=saved

I've tried running update-grub2 and this is the output:
Found linux image: /boot/vmlinuz-3.2.0-20-generic
Found initrd image: /boot/initrd.img-3.2.0-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu precise (development branch) (12.04) on /dev/sda5
Found Windows 7 (loader) on /dev/sdb1
done

YET when I reboot there is still no windows option!!

Pls help!

---

### Post by Quackers on 2012-04-11
Is the grub menu that you are seeing taking up the whole of the screen? Try pressing the down arrow and see if the Windows entries appear.

---

### Post by oldfred on 2012-04-11
If anything is wrong, the new grub 1.99 is not so tolerant of typos. I had a typo in my 40_custom for a long time and it just did not show one boot stanza that I did not realize was not there. With grub 1.99, it would not write a new grub.cfg but created /boot/grub/grub.cfg.new as the error file. Even extra spaces at the end of a line can cause issues.

Grub 1.99 40_custom
Does not like typos,changed root to set root, cannot have echo, cat, EOF lines
[http://ubuntuforums.org/showthread.php?t=1746868](http://ubuntuforums.org/showthread.php?t=1746868)
/boot/grub/grub.cfg.new

---

### Post by dragin33 on 2012-04-11
A window called debconf randomly appeared on my dekstop saying "configuring grub-pc."  The help says that grub was previously installed to a disk that is no longer present.  Perhaps this is due to the intel raid somehow?  It lists sda, sdb, and and sda5 which is my linux partition.

I don't really have a lot of time to fiddle with this I think I'll throw the CD in and reformat it.  Hopefully that will fix me.

---

### Post by dragin33 on 2012-04-12
I deleted the linux partitions and completely reinstalled and this time the system wouldn't even boot to Ubuntu (Although the windows item was back in the menu.)  Grub came up, The Ubuntu logo started but then it crashed and went into busybox or whatever.

In the end I think that Ubuntu hates being on a FAKERAID system let alone being dual booted along with Windows 7.  Stay away from Ubuntu + Fakeraid I guess.

---

### Post by jadtech on 2012-04-12
there are many who use computers everyday who would give anything for windows to just  disappear  :)

---

