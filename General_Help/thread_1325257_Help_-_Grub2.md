---
title: "Help - Grub2"
date: 2009-11-13
forum: General Help
---

### Post by Quarkrad on 2009-11-13
Just installed 9.10 on friends PC.  I used a 2nd HD to install 9.10 - so I now have Master/sda/Ubuntu 9.10 and Slave/sdb/WinXP.   This is my error:  prior to the new HD/Ubuntu there was an error on the windows HD.  It use to have both winXP and Vista but we took off Vista some time ago.  However, when the PC booted it offered the choice to go winXP or Vista (although Vista wasn't there!).  I should have corrected but due to laziness left it.  So when I put in the new HD and installed 9.10 Grub now has an entry at the bottom called **Windows Vista (loader) (on dev/sdb1)**.  If I choose that entry I get the message  **error invalid signature**.    So I took out the 9.10 hd, booted into windows and corrected the Vista entry error.   The windows hd  now boots straight to winXP without any screen offering winxp/Vista to boot to.  Now when I put the 2nd 9.10 HD back in the machine I get the same grub with a Vista option and the same error.  This is logical but I need to edit Grub2 to read WinXP and point to the right place.  What do I do?

---

### Post by ranch hand on 2009-11-13
You have got a really screwy system.  I thought that was something I just did.

First have you run;
```

sudo update-grub

```
since you made your corrections?

If not do so and report back.

---

### Post by hwttdz on 2009-11-13
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Quarkrad on 2009-11-13
Thanks for help.  This is what I get re up dating grub:

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

---

### Post by Quarkrad on 2009-11-13
l also tried this:

update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Should I take out the new HD/9.10 and install grub on the winXP HD?  If so I assume this is grub2?

---

### Post by ranch hand on 2009-11-13
If you are using a clean install of 9.10, yes it is grub2.

I would take a look at the link in my sig.  And at the links in it.  At least the first three.

If you run down the links you will see one refering to recovering with live CD.  I would give this a whack.

---

