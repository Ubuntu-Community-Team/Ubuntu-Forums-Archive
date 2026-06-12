---
title: "Help wiping hard drive clean"
date: 2011-01-21
forum: General Help
---

### Post by pellpell4 on 2011-01-21
I've been trying to put windows xp on my computer that I currently have ubuntu installed on. I haven't found any easy way to do it. I found the command "sudo dd if=/dev/zero of=/dev/XdY" and decided to just wipe the drive clean. when I start the computer now it goes to...
 
"Press any key to boot from CD.....error: unknown filesystem.
Grub rescue>"
 
I can boot from the XP cd, but it's apparently still a Linux partition on the hard drive because it keeps erroring out like it used to. Since the Grub Rescue is on there I'm assuming the hard drive didn't get wiped clean. Where to I go from here to get to the point of being able to install windows?

---

### Post by pellpell4 on 2011-01-21
bump, any help is appreciated, I just want the hard drive cleared for windows :(

---

### Post by PRC09 on 2011-01-21
I am assuming that the error is after you Press Any Key and if so it means that your machine is not reading your XP disk and trying to boot to the next device in boot order.

---

### Post by pellpell4 on 2011-01-21
> **PRC09 said:**
> I am assuming that the error is after you Press Any Key and if so it means that your machine is not reading your XP disk and trying to boot to the next device in boot order.
 
no i can boot from the windows disc, but it won't install because there's no ntfs partition

---

### Post by Spyderkid on 2011-01-21
If you put the Xp disk in boot it up and then you can delete the ubuntu partition just delete all of them if you don't need to keep any

---

### Post by cgb on 2011-01-21
The XP install should give you an option to delete the existing partition and create a new NTFS partition and format.  This should get you straightened up.

---

### Post by pellpell4 on 2011-01-21
> **cgb said:**
> The XP install should give you an option to delete the existing partition and create a new NTFS partition and format. This should get you straightened up.
 
The cd loads a bunch of drivers and thing and as soon as it says "starting windows" at the bottom it gives me a blue screen telling me to check the hard drive and restart to try again.

---

### Post by efflandt on 2011-01-21
If you are trying to erase your "only" internal hard drive, that should typically be **sudo dd if=/dev/zero of=/dev/sda**.  Although, unless you have something you want nobody to recover, it is usually sufficient to do **sudo dd if=/dev/zero of=/dev/sda count=2K** to erase 1 MB at the beginning of the drive including the mbr (grub) and partition table.  Then you should not get any grub error (grub will not exist) and the drive should appear to be brand new to any partitioner.

But if you have multiple internal drives, you have to be "very" careful about which drive you are erasing and which drive your system is actually booting from (in CMOS setup), because you do not want to erase a drive you want to keep.

It sounds like maybe you erased a partition (like /dev/sda1?) instead of the drive (/dev/sda).  In that case, grub would still be in the mbr and the partition table may point to a partition that no longer exists, so it appears to be a corrupt partition table to Windows.

---

### Post by MooPi on 2011-01-21
If you have the live CD for Ubuntu you can try shred. From terminal ```
sudo fdisk -l
```
This should give you the drive designation, something like /dev/sda or /dev/sdb.
```
shred -v -n1 /dev/sdx
``` This command will wipe the drive once and show progress.

---

### Post by pellpell4 on 2011-01-21
> **efflandt said:**
> If you are trying to erase your "only" internal hard drive, that should typically be **sudo dd if=/dev/zero of=/dev/sda**. Although, unless you have something you want nobody to recover, it is usually sufficient to do **sudo dd if=/dev/zero of=/dev/sda count=2K** to erase 1 MB at the beginning of the drive including the mbr (grub) and partition table. Then you should not get any grub error (grub will not exist) and the drive should appear to be brand new to any partitioner.
 
But if you have multiple internal drives, you have to be "very" careful about which drive you are erasing and which drive your system is actually booting from (in CMOS setup), because you do not want to erase a drive you want to keep.
 
It sounds like maybe you erased a partition (like /dev/sda1?) instead of the drive (/dev/sda). In that case, grub would still be in the mbr and the partition table may point to a partition that no longer exists, so it appears to be a corrupt partition table to Windows.
 
The second code sounds perfect, would I have to reinstall Ubuntu to do that though since I can't get passed the grub rescue screen?

---

### Post by psusi on 2011-01-21
The drive does not have to be clean to install Windows.  If it errors trying to access the drive, then it is because it needs an updated driver.  Otherwise you just get to the partitioning screen and blow any existing one away and create one for windows.

---

### Post by efflandt on 2011-01-21
You should be able to boot an Ubuntu install CD to a live system.  But you might need to still press a key during the BIOS splash screen, even if you set DVD/CD before hard drive in BIOS.

Or drive manufacturers often have a disk utility self booting CD iso that can write zeros to the drive (for example DataLifeguard for WD drives).

---

### Post by pellpell4 on 2011-01-24
by using "sudo dd if=/dev/zero of=/dev/XdY" would that wipe out my manufacturer's drivers? I'm unable to boot from the Ubuntu live CD on that computer, and can only get as far as "starting windows" on the windows install CD, before it errors out and tells me there's a hard drive issue. I know the hard drive is good, so either there's a partitioning issue still, or the computer just isn't recognizing the drive in general because of the driver.

---

### Post by CharlesA on 2011-01-24
Sounds like you don't have the SATA drivers for the hard drive controller. If you still have a recovery partition, you can use that otherwise you'll have to find the drivers and slipstream them onto the windows xp cd.

---

