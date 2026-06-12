---
title: "GRUB trouble"
date: 2011-12-15
forum: General Help
---

### Post by u-noob-tu on 2011-12-15
The other day i installed Kubuntu 11.10 to an external HDD. I guess at some point during the installation, i installed the bootloader to that external drive. now i cannot boot into Ubuntu (which is in my laptop's internal drive) without the external drive being on. GRUB does not appear if it is not on during boot (i get a message saying "No such device 'some-really-long-number'. GRUB Rescue>"). I tried installing GRUB on my Ubuntu install and generating a grub.cfg and sudo update-grub, but it still does not show at boot. is there anyway i could get the bootloader back over to my internal HDD without having to reinstall everything?

---

### Post by warehouse@karmickoala on 2011-12-15
When You Switch Your Computer On, Can You Boot Into Any OS ?

---

### Post by seawolf167 on 2011-12-15
If you unplug your external drive, then follow [this guide ]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")to reinstall Grub2 on your internal HDD you'll be able to boot to that drive, then once that is booting properly, run

```
sudo update-grub
```from a terminal to pick up the other install.

If for some reason after you reinstall Grub you still cannot boot to your internal drive, then you'll need to purge and reinstall Grub2 following [this guide]("http://ubuntuforums.org/showthread.php?t=1581099").

---

### Post by u-noob-tu on 2011-12-15
> **warehouse@karmickoala said:**
> When You Switch Your Computer On, Can You Boot Into Any OS ?
Not without the external drive being on, no i cant.

---

### Post by seawolf167 on 2011-12-15
> **u-noob-tu said:**
> Not without the external drive being on, no i cant.

Did the Grub reinstall work? If not, did the purge and reinstall of Grub work?

---

### Post by u-noob-tu on 2011-12-15
Im trying your first suggestion now. Using Boot-repair.

---

### Post by u-noob-tu on 2011-12-15
boot-repair worked great. was able to boot from internal drive with no trouble.

---

### Post by seawolf167 on 2011-12-15
> **u-noob-tu said:**
> boot-repair worked great. was able to boot from internal drive with no trouble.

Now that you can boot from your internal drive, run 

```
sudo update-grub
```

to pick up on your other [external] drive's installation. You can leave grub on the external drive in case you bring it to another computer, just ensure that in BIOS the 1st priority boot device is your internal drive and not an external drive and you will be fine.

If everything is then working, please mark this thread as solved

---

