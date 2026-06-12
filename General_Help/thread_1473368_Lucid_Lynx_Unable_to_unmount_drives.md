---
title: "Lucid Lynx Unable to unmount drives"
date: 2010-05-05
forum: General Help
---

### Post by yahelos on 2010-05-05
Hello

Ive done a clean install of Lucid and now i can unmount any drive (flash or partition).

the error ive got is "umount: /media/disk is not in the fstab (and you are not root)"

Im the only one  (so i bevieve im the root). Im using the same system from feisty fawn without provlem.

PS my disk are NTFS

---

### Post by amsterdamharu on 2010-05-05
I don't think you are root or it would be allowed, in a terminal you can type the command whoami to see what user you are.

Strange you can mount them (maybe automount) but not unmount, can you post the contents of the file:
/etc/fstab

Somewhere ubuntu added the need of a password for mounting partitions in nautilus, you can get rid of that by changing some policy, see this thread second post:

[http://ubuntuforums.org/showthread.php?t=1307383](http://ubuntuforums.org/showthread.php?t=1307383)

---

### Post by yahelos on 2010-05-05
Im the only one user...how i cant be root?

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=47eff7d8-1308-432b-bba0-44dd071084c7 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

As for the second part the file with policies is totaly blank.

---

### Post by yahelos on 2010-05-05
as you see in the photo Sandisk cruzer is my flash driver. The 38Dblahblah as mounted the error and the blank file

[[URL=http://img710.imageshack.us/i/screenshotsus.png/][IMG]http://img710.imageshack.us/img710/6387/screenshotsus.th.png[/IMG]]("http://img535.imageshack.us/i/screenshotwfx.png/")

[/URL]

---

### Post by OpSecShellshock on 2010-05-05
The disk is probably owned by root. Have you tried using sudo before the unmount commands to elevate privileges? That will work short term. I do think it's odd that it brings up the fstab error, since I've never had to add removable storage to fstab in order to mount/unmount it as a regular user. In Lucid you can usually right click on the desktop icon and select "safely remove" or whatever it says now.

Out of curiosity, are you able to save files to that drive and/or copy files to it from the internal hard disk?

---

### Post by yahelos on 2010-05-05
the error comes out from "right click -> unmount". Yes i can transfer files from and to the disks.

---

### Post by yahelos on 2010-05-05
ihave download some mount toolz from synaptics and now with right clik -> eject from :My computer" i can unmount the drives. From desktop I cant.

Its a solution of some kind!!

I dl several toolz so i dont really know which one did the dirty work

---

### Post by amsterdamharu on 2010-05-05
Press alt + F2 and type gksu gedit /etc/fstab
Make sure none of the user mounted partitions are in the fstab, only the ones that the system needs, in your case / none and /media/floppy0 (second column):
```

UUID=47eff7d8-1308-432b-bba0-44dd071084c7 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Stay away from disk utilities, lucid has palpino disk utility or something like that to mount partitions but you don't need it. In nautilus you can just click on the partitions to mount them and right click to unmount.

Partitions mounted as normal user by nautilus should just unmount without a problem.

---

### Post by cariboo on 2010-05-05
This really isn't a security question. Moved to General Help

---

### Post by seeker5528 on 2010-05-05
> **yahelos said:**
> the error ive got is "umount: /media/disk is not in the fstab (and you are not root)"

Im the only one  (so i bevieve im the root). Im using the same system from feisty fawn without provlem.

This solution from [another thread](http://ubuntuforums.org/showthread.php?t=1470049) sounds like it is what you are probably looking for......

From a terminal window type

```
sudo apt-get remove --purge usbmount
sudo apt-get install pmount
```

Usbmount doesn't show up for me as a missing recommends, but it seems to be showing up on peoples boxes. Don't know if it is because it is part of the OOBE or if it is something people are installing after the fact while looking for a solution.

Later, Seeker

---

### Post by yahelos on 2010-05-06
Ive install lucid to another machine and with the same usb sticks, the system auto mount them into the desktop and i can unmount them without problem.

In my "prblematic" pc it doesnt mount them automaticly into desktop (i need to go to "my computer" to open the flash disk" and it doesnt unmount them from the desktop with the error.
 
If i select "safetly remove device" from inside "my computer" i can unmount them

So my problem has been solved (in some way)

---

### Post by akrobert on 2010-05-29
I had the same problems...here was the thread that fixed it

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1469499](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1469499)

Robert

---

### Post by Plin on 2010-06-25
Well i had the same problem since my last updated in Lucid Lynx, then couldn't mount automaticly my external USB HDD.

I tried EVERYTHING, and after spent hours searching, i found the solution: Install MountManager, trought  Synaptic Package Manager. Then, in System/Administrator/MountManager i was able to mount the drive normally.

That's worked for me... i hope it worke for u too...

¡See ya!
:p

Plin

---

