---
title: "Windows 7 Upgrade"
date: 2009-10-24
forum: General Help
---

### Post by dhavalbbhatt on 2009-10-24
Hi all,

I am looking to upgrade my desktop, which has 2 hard drives. One of the HDD is partitioned with Ubuntu 9.04 and Vista. The other is only Ubuntu 9.04. The question for the forum is if I were to upgrade Vista to Windows 7, will the Windows upgrade overwrite my Grub?

Right now, my main HDD is the one with only Ubuntu - implying the Grub resides there(?). Please let me know if I need to post anything for this forum to answer my questions. I will be more than happy to do so.

Thanks,
DB

---

### Post by barthel on 2009-10-24
It's possible. Microsoft isn't known for playing nicely with others. The last time I did something like that, I installed MS-Windows first, then set up my dual-booting Linux.

Personally, I'd make sure I had good backups then give it a shot. If 7 behaves, no problem. If it doesn't, at least you've only lost the time required to restore from your backups.

---

### Post by rockstarrem on 2009-10-24
It is known to overwrite GRUB, yes. You can fix this by reinstalling GRUB though via the live CD.

---

### Post by flipper9 on 2009-10-24
Yes; Microsoft doesn't care what is installed on your system and will overwrite any bootloader without warning or asking you before hand.  You'll need to restore your GRUB configuration and reinstall the GRUB bootloader after reinstalling/upgrading Windows.  How to do that, you'll need to look that up or maybe someone will search for you.

---

### Post by donsy on 2009-10-24
Boot from live CD and open up a Terminal window. Then:
```

sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)
quit
```

---

### Post by dhavalbbhatt on 2009-10-24
Thanks all for your replies. I will consider this thread solved.

Once again, much appreciated.

---

