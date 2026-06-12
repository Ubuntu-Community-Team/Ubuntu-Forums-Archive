---
title: "command line alternative for &quot;Safely Remove Drive&quot;"
date: 2011-08-09
forum: General Help
---

### Post by balance07 on 2011-08-09
Ubuntu Server 10.04 LTS

Is there a command line alternative to clicking on "Safely Remove Drive" in nautilus?

When I click on "Safely Remove Drive" in nautilus, the USB HDD attached (WD Elements) vanishes from the nautilus "places" list, the drive spins down, and the light on the drive dims to indicate that it is powered down.

I have tried the "umount" command as well as the "eject" command from the terminal, but they both only seem to unmount the drive, as it is still shown in the nautilus "places" list and the light on the drive stays bright.

is there another way? thanks!

---

### Post by xiainx on 2011-08-09
sudo umount /media/<name of HDD>

---

### Post by balance07 on 2011-08-09
thanks for the reply, xiainx.  i should have mentioned that i tried 'umount' before 'eject', and that they both seem to do the same thing, unmount only, and not power down the usb drive.

---

### Post by mc4man on 2011-08-09
You should really  d. check this, just what I've observed here
Ex.I have a usb drive, sdb with 1 partition sdb1

So to 'Safely  remove' from cli - 
```
udisks --unmount /dev/sdb1 && udisks --detach /dev/sdb
```

see man udisks for more info, ect.

---

### Post by balance07 on 2011-08-09
YES!

thanks mc4man, that did the trick!

---

### Post by paradoja on 2012-12-04
Thanks a lot!!!!!!!

---

### Post by oldos2er on 2012-12-04
Old thread closed.

---

