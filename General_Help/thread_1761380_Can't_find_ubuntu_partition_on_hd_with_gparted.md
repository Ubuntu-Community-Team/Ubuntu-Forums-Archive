---
title: "Can't find ubuntu partition on hd with gparted"
date: 2011-05-18
forum: General Help
---

### Post by penguinslide on 2011-05-18
Hi, I have a laptop with dual boot and I think because it is a dual boot I can't find the linux partition, installed when I knew nothing about linux, so I most likely went with the default settings, I'm an absolute convert now and have run out of space for ubuntu.

So got on the net and seen many screen shots of gparted with a clearly visible linux partition, swap etc, so I make myself a gparted live cd and mine is just not there.

 Really don't want to do another ubuntu reinstall !! This k52f has too many setting to correct with ubuntu and took me a really long time!! 

Or is there is a different solution to to this other than expanding a possibly hidden linux partition? Is the alternative storing files on a shared partition both os can share?

---

### Post by Dáire Fagan on 2011-05-18
> **penguinslide said:**
> Hi, I have a laptop with dual boot and I think because it is a dual boot I can't find the linux partition, installed when I knew nothing about linux, so I most likely went with the default settings, I'm an absolute convert now and have run out of space for ubuntu.

So got on the net and seen many screen shots of gparted with a clearly visible linux partition, swap etc, so I make myself a gparted live cd and mine is just not there.

 Really don't want to do another ubuntu reinstall !! This k52f has too many setting to correct with ubuntu and took me a really long time!! 

Or is there is a different solution to to this other than expanding a possibly hidden linux partition? Is the alternative storing files on a shared partition both os can share?

Please post the output of df -h in terminal, and describe in your own words what partitions you believe to exist, or should there simply just be one Ubuntu, and one.... Windows?

My largest partition is NTFS so I can share it across different operating systems.

---

### Post by garvinrick4 on 2011-05-18
> **penguinslide said:**
> Hi, I have a laptop with dual boot and I think because it is a dual boot I can't find the linux partition, installed when I knew nothing about linux, so I most likely went with the default settings, I'm an absolute convert now and have run out of space for ubuntu.

So got on the net and seen many screen shots of gparted with a clearly visible linux partition, swap etc, so I make myself a gparted live cd and mine is just not there.

 Really don't want to do another ubuntu reinstall !! This k52f has too many setting to correct with ubuntu and took me a really long time!! 

Or is there is a different solution to to this other than expanding a possibly hidden linux partition? Is the alternative storing files on a shared partition both os can share?
You maybe have a WUBI install, look in your C: drive of windows and see if there is not
a folder called Ubuntu right next to Users. 
You can run this in Ubuntu and will give you your paritions:
```
sudo fdisk -l
``` (lower case L)
Here is link for Wubi:
[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide#Introduction")

---

### Post by Dáire Fagan on 2011-05-18
> **garvinrick4 said:**
> 
You can run this in Ubuntu and will give you your paritions:
```
sudo fdisk -l
```


I was just going to add output of that wouldn't hurt either :)

---

### Post by penguinslide on 2011-05-18
> **dusf said:**
> I was just going to add output of that wouldn't hurt either :)

Wow thanks for the fast replies, wasn't expecting one for hours!!


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2167    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2168       41335   314616411+   7  HPFS/NTFS

df -h gives:

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             29G   19G  8.7G  69% /
none                  2.9G  272K  2.9G   1% /dev
none                  2.9G  600K  2.9G   1% /dev/shm
none                  2.9G   92K  2.9G   1% /var/run
none                  2.9G     0  2.9G   0% /var/lock
none                  2.9G     0  2.9G   0% /lib/init/rw
/dev/sda2             301G   75G  226G  25% /host

And yes ubuntu is visible from windows

If I could see how you post screen shots here other than an url I would. Thanks!!

---

### Post by penguinslide on 2011-05-18
> **dusf said:**
> Please post the output of df -h in terminal, and describe in your own words what partitions you believe to exist, or should there simply just be one Ubuntu, and one.... Windows?

My largest partition is NTFS so I can share it across different operating systems.

I have seen it earlier in terminal using df -h, but in a partition editor I can't.

Is the NTFS automatically shared between os or is there something I must do to enable this?

---

### Post by mcduck on 2011-05-18
> **penguinslide said:**
> Wow thanks for the fast replies, wasn't expecting one for hours!!


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2167    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2168       41335   314616411+   7  HPFS/NTFS

df -h gives:

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             29G   19G  8.7G  69% /
none                  2.9G  272K  2.9G   1% /dev
none                  2.9G  600K  2.9G   1% /dev/shm
none                  2.9G   92K  2.9G   1% /var/run
none                  2.9G     0  2.9G   0% /var/lock
none                  2.9G     0  2.9G   0% /lib/init/rw
/dev/sda2             301G   75G  226G  25% /host

And yes ubuntu is visible from windows

If I could see how you post screen shots here other than an url I would. Thanks!!

That's definitely a Wubi  install (Ubuntu being installed into a file inside the Windows filesystem instead of having it's own partition). So you can't find the Ubuntu partition in Gparted because there isn't one.

I haven't got much experience with Wubi installs, so I can't really say how to increase the available space after install, or if that's even possible.

---

### Post by -kg- on 2011-05-18
My observation is that you installed Ubuntu using WUBI.  GParted should be able to "see" a partition, hidden or not.

To post a screenshot, you would use the "Insert Image:" tag (the button with the portrait next to the "Quote" button above).  You'll need to post the image to Photobucket or another hosting site, I'm assuming.

At any rate, the command, "sudo fdisk -l" would have shown the Ubuntu partition, whether GParted showed it or not.  Since it wasn't shown as an output of that command, it doesn't exist, and therefore, you must have installed via WUBI.

---

### Post by penguinslide on 2011-05-18
> **mcduck said:**
> That's definitely a Wubi  install (Ubuntu being installed into a file inside the Windows filesystem instead of having it's own partition). So you can't find the Ubuntu partition in Gparted because there isn't one.

I haven't got much experience with Wubi installs, so I can't really say how to increase the available space after install, or if that's even possible.

I'm really hoping it is possible, even if I could take it out and maybe put it into a new partition? Is there Linux application to do this or maybe from terminal?

---

### Post by garvinrick4 on 2011-05-18
Windows is /host and Wubi is the guest:
> [COLOR=Red]/dev/loop0[/COLOR]             [COLOR=Red]29G   19G  8.7G  69% /[/COLOR]
none                  2.9G  272K  2.9G   1% /dev
none                  2.9G  600K  2.9G   1% /dev/shm
none                  2.9G   92K  2.9G   1% /var/run
none                  2.9G     0  2.9G   0% /var/lock
none                  2.9G     0  2.9G   0% /lib/init/rw
[COLOR=Red]/dev/sda2             301G   75G  226G  25% /host[/COLOR]


Link on Wubi:
[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide#Introduction")

---

### Post by penguinslide on 2011-05-18
> **garvinrick4 said:**
> Windows is /host and Wubi is the guest:

Link on Wubi:
[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide#Introduction")

Thanks, some links off that link that look promising, I should have asked this question on ubuntu forums weeks ago!!

Solution found: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Thanks everyone

---

