---
title: "Remove write protection from partition"
date: 2010-05-15
forum: General Help
---

### Post by Wee_Guy on 2010-05-15
I'm trying to create a bootable HFS+ partition.
I've succeeded in creating the HFS+ partition in Windows using Mac Drive 8, but need to set the partition to "Active" to be able to install an OS on it. The issue lies that when I try to set it to active in windows disk management it tells me that the media has been write protected by Mac Drive.
I want to either set the partition as active (or at least disable write protection to allow me to set it as active in windows) or find another means of creating an HFS+ partition, which I know gparted claims to do but I can't manage to enable it.

I'm currently running Windows 7 but I have Ubuntu 9.04 Live CD to use if necessary.

Thanks in advance for your help.

---

### Post by conradin on 2010-05-15
I would modify the permissions, and or ownership with chmod or chown.
First i would want to know what partition I was editing, so i would do:
```

sudo fdsik -l

```
Then I would determine what permissions I want the disk to have.
and apply that with chmod
```

sudo chmod [permisions] [device]

```

Gparted can work with man filesystems but only comes by default with a few.
in the synaptic package manager, type the filesystem type you want to add. 
in your case, hfsplus.

you should then have access to those tools in Gparted.

---

### Post by Wee_Guy on 2010-05-15
Thanks conradin, I tried your advice but Windows still won't change it. Maybe it's Windows that's messed up...

I've tried to set up the HFS+ patch thing on a Live USB stick but for some reason I can only get HFS working, which I can't use due to it being limited to a 2Gb filesystem.

I'm going to try installing Ubuntu on the disk and enable HFS+ on that. I'm getting pretty tired of Windows now anyway.

---

