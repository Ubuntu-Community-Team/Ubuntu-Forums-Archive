---
title: "Chaning Mount Point of Drive"
date: 2010-05-23
forum: General Help
---

### Post by thunderbox on 2010-05-23
I just removed ubuntu and installed kubuntu, just for something different. i had my home and / folders partitioned separately for ease of upgrade, now during the update process i forgot to make sure the home directory would mount the right partition. for fear of loosing data, so my question is, is there any way of changing the mount point of the drive one the OS is installed.

EDIT. sorry about spelling mistake(s)

---

### Post by spiky001 on 2010-05-23
you can use gparted to mount home

---

### Post by wieman01 on 2010-05-23
All mount points can be found and changed here
> cat /etc/fstab
Open that file with a text editor and change the corresponding line. Post the contents here if you need support.

---

### Post by thunderbox on 2010-05-23
Output of the cat /etc/fstab . its only listing 2 partitions, ive got a 15gig one with the OS on it, then the home and then the swap.

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=412737cb-5230-4c71-bab2-fd882ebc2b2b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e9bff9ac-e479-4e9e-9857-f077e900ee46 none            swap    sw              0       0


---

### Post by mikewhatever on 2010-05-23
You'll need to post some more info to be able to get help on this, namely the outputs of the following:

sudo fdisk -l

sudo blkid

---

### Post by jamesisin on 2010-05-23
On a typical installation /home is assumed to be under / and thus won't have its own mount point.  If you provide the output mikewhatever asks for we can help you create the proper fstab entry for your configuration.

---

### Post by thunderbox on 2010-05-23
sudo fdisk -l:

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b18b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14647296   83  Linux
/dev/sda2            1824       38914   297921537    5  Extended
/dev/sda5           37434       38914    11885568   82  Linux swap / Solaris
/dev/sda6            1824       37434   286034944   83  Linux


and

sudo blkid

> /dev/sda1: UUID="412737cb-5230-4c71-bab2-fd882ebc2b2b" TYPE="ext4" 
/dev/sda5: UUID="e9bff9ac-e479-4e9e-9857-f077e900ee46" TYPE="swap" 
/dev/sda6: UUID="d15dea59-4249-46b1-b54f-de185e033ab6" TYPE="ext4"

---

### Post by jamesisin on 2010-05-23
I suppose you want to add something like this at the bottom of fstab:

```
# here is my boot mount for /home
UUID=d15dea59-4249-46b1-b54f-de185e033ab6 /home ext4 errors=remount-ro 0 1
```

You can edit fstab using gedit:

```
gksudo gedit /etc/fstab
```

But wait until someone smarter than me chimes in...

---

### Post by wieman01 on 2010-05-24
jamesisin, 

I believe you are almost right, way to go. This is based on my fstab entry for /home, you would need to add these 2 lines:
> # /home was on /dev/sda6 during installation
UUID=d15dea59-4249-46b1-b54f-de185e033ab6 /home           ext4    defaults        0       2

I assume that your /home is on **/dev/sda6** with ID **d15dea59-4249-46b1-b54f-de185e033ab6**.

---

### Post by jamesisin on 2010-05-24
What's the difference between the 0 2 and the 0 1?

---

### Post by thunderbox on 2010-05-24
> **jamesisin said:**
> I suppose you want to add something like this at the bottom of fstab:

```
# here is my boot mount for /home
UUID=d15dea59-4249-46b1-b54f-de185e033ab6 /home ext4 errors=remount-ro 0 1
```You can edit fstab using gedit:

```
gksudo gedit /etc/fstab
```But wait until someone smarter than me chimes in...

That solution worked perfectly, is there any need to change it (unless the 1 and the error=remount makes any difference

---

### Post by thunderbox on 2010-05-24
also is there a way to make my drives auto mount, i have an external hard drive, on my Ubuntu it was auto mounting (which i want) since I've gone to KDE, it doesn't. can i fix that in that text document somehow?

---

### Post by jamesisin on 2010-05-24
I suppose you could.  Add another line in fstab for the device (you should be able to sort out the details from what we've already done).  Here is an article I wrote about adding additional drives which will also help:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

You will not want to use the remount argument in case the drive happens to be unplugged.

---

### Post by thunderbox on 2010-05-26
I used KDE's partition manager to change how the drive mount (set them all to automount on login) adds a small delay to loggin in but it means my music collection is found as soona s i open amarok. thanks for all your help

---

### Post by jamesisin on 2010-05-26
Of course you could create a launcher (for Amarok) where it actually ran a script that tested for the mounted drive.  If the drive were mounted, it would start Amarok; if the drive were not mounted it would provide an error.

---

