---
title: "DualBoot, No xp after updates"
date: 2009-11-27
forum: General Help
---

### Post by ALnot on 2009-11-27
I have a dual boot with Ubuntu /xp.
I had 9.04 - worked great with dual boot.
I put on 9.10 - worked great.
The other day I updated 9.10 and now my boot menu blinks.
I have Vista on one hdd, server2008 on another and Ubuntu/xp on a 3rd.

These are the new entry's on my boot list:

windows vista(loader)(on/dev/sda1)
windows vista(loader)(on/dev/sdb1)
microsoft windows xp professional (on/devsdc1)

When I select xp I get this error:

error: invalid signature.

When I select Ubuntu it boots just fine, like always.

Is there a simple fix for this?

Thanks ALnot.

---

### Post by kestrel1 on 2009-11-27
You could try getting grub to make the menu again. This may or may not work. Type: ```
sudo update-grub2
```
This should regenerate the list.

---

### Post by ALnot on 2009-11-27
I ran: sudo update-grub2 and this is what happened -

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Found Microsoft Windows XP Professional on /dev/sdc1
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

done

Not sure what this means???
ALnot.

---

### Post by kestrel1 on 2009-11-27
Have a look at this thread. Seems to be a similar problem:
[http://ubuntuforums.org/showthread.php?p=8258932](http://ubuntuforums.org/showthread.php?p=8258932)
The suggestion near the bottom about using GAG may solve the problem.

---

### Post by ALnot on 2009-11-27
I downloaded GAG, but I think I'll back burner this headache for a while.
I'm going to mark as solved.
thanks for the Help

ALnot

---

### Post by kestrel1 on 2009-11-27
I will do a bit more research & see if I can come up with a better solution & let you know.

---

### Post by namok on 2009-11-27
```
sudo grub-mkdevicemap
sudo update-grub2
```

---

