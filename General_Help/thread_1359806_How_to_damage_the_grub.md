---
title: "How to damage the grub?"
date: 2009-12-20
forum: General Help
---

### Post by OldGrantonian on 2009-12-20
I have dual-boot XP and Karmic.

I want to practice restoring grub, using the following thread:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I would be grateful if someone could tell me an easy way to "wipe" the grub. For example, re-installing XP will damage the grub, but I'm sure there are quicker ways to do the same thing :)

BTW:  We were taught at school that roast pork was originated by the Chinese. A pig pen burnt down, and the Chinese discovered that the roast pork was delicious. So, they all started burning down their pig pens :)

Eventually, a search on the forums showed that they could simply roast the pig on a barbecue :)
.

---

### Post by Leppie on 2009-12-20
you could try to change your device.map:
```
$sudo cp /boot/grub/device.map /boot/grub/device.map.old
```
now open the device.map with an editor:
```
$gksudo gedit /boot/grub/device.map
```
change the link to a disk you do not have installed (if you have only one disk installed, then anything not pointing to sda will be good):
```
(hd3)	/dev/sdd
```
save and close the file. then re-install grub:
```
$sudo grub-install --force
```

i've never tried this though, sometimes breaking things intentionally is harder than breaking them by accident ;)

---

### Post by john newbuntu on 2009-12-20
Damaging the Grub. Now, that's something new.  We have a handy dandy command to do this and is called "dd".

---

### Post by Leppie on 2009-12-20
> **john newbuntu said:**
> Damaging the Grub. Now, that's something new.  We have a handy dandy command to do this and is called "dd".

do you have the complete command?

---

### Post by nikhilbhardwaj on 2009-12-20
search for it
you'll find it
(**if** can be /dev/zero and **of** your partition but you may end up wiping your hd if you aren't careful)
another would be to run fixmbr from your windows xp cd

---

### Post by Leppie on 2009-12-20
think i just found it:
```
$dd if=/dev/zero of=/dev/sda bs=446 count=1
```

**_of course, first back up the mbr:_**
```
$dd if=/dev/sda of=~/oldmbr.img bs=446 count=1
```

---

### Post by SecretCode on 2009-12-20
For example, ["Using dd to zero the MBR" query. - LinuxQuestions.org](http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query.-606489/) - note especially using bs=446 to avoid wiping out the partition table.

Unless that's what you want to do, of course.

---

### Post by Leppie on 2009-12-20
> **SecretCode said:**
> For example, ["Using dd to zero the MBR" query. - LinuxQuestions.org](http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query.-606489/) - note especially using bs=446 to avoid wiping out the partition table.

Unless that's what you want to do, of course.

thanks for that, updated my post accordingly

---

