---
title: "Auto Mounting Removable Drives"
date: 2012-07-04
forum: General Help
---

### Post by Mojosdad on 2012-07-04
I've upgraded from 10.04 to 11.10 to 12.04 and now I seem to have lost the ability to have my USB drives mount to /media/<volume name>. I can mount manually via fstab; drives are recognised by system (fdisk) and nautilus will mount to usb0 etc (although I can't unmount as not root).

But I would really like the old behaviour of mounting to a recognisable name for each disk. Does anyone know how to resolve without an fstab entry for each disk? Seems like lots of removable drive problems but the solutions I have tried so far are not making a difference.

I have had to add the pmount package (that I'm certain was in my 11.04 install as well as samba which also seemed to be missign after upgrade - what else might be gone) which I thought would solve the problem but no luck.

---

### Post by cipherboy_loc on 2012-07-04
Have you named your flashdrives (with a label)? Generally nautilus will mount in /media/label, unless you don't have a label on the device, which it will then default to an ID of sorts, depends on filesystem type.

Cipherboy

---

### Post by Mojosdad on 2012-07-05
Yes, drives have labels - they were being mounted as per label in 11.04, but not after 12.04 upgrade

---

### Post by cipherboy_loc on 2012-07-05
What does
```

gvfs-mount --list

```
Return?


Cipherboy

---

### Post by coffeecat on 2012-07-05
> **Mojosdad said:**
> 
I have had to add the pmount package

That might be part of the problem. You shouldn't need it. Some (all) of the 3rd party mounting apps interfere with the automounting functionality built into the GUI. Try uninstalling it. Also usbmount if you've installed that and anything similar.

---

### Post by Mojosdad on 2012-07-05
That command give no output at all:

mojosdad@mypc:~$ gvfs-mount --list
mojosdad@mypc:~$

---

### Post by cipherboy_loc on 2012-07-05
Did you have your drives plugged in? And follow coffeecat's suggestion.

---

### Post by Mojosdad on 2012-07-05
Yes the drive was in at boot and used to be recognised on every restart (I have never hasd to remove the drive since I first plugged it in).On reboot is now not mounted, I unplug and re-plug, still not mounted.

Mount by hand (via fstab and mount -a I get:

mojosdad@mypc:~$ gvfs-mount --list
Mount(0): WD_2Tb_1 -> file:///media/WD_2Tb_1
  Type: GUnixMount

the location is the mount point I have had to set up myself

---

