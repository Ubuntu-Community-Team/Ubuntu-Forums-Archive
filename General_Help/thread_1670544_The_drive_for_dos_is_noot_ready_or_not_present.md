---
title: "The drive for /dos is noot ready or not present"
date: 2011-01-19
forum: General Help
---

### Post by axept on 2011-01-19
Every time I boot up I get this message.

First time I got that message was after a reboot I had to take after my laptop was up and running for 22 days...

I can't see in GParted that any partition is mounted as /dos ??

Any Idea ?

Edit: I deleted the hidden win7 partition a few days ago because grub listed win7 in the menu, but I did update grub afterwards. Is it possible that is the reason ? I don't know..

Edit 2: I can see in fstab that its present there..

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext3    errors=remount-ro 0       1
# /dos was on /dev/sda2 during installation
UUID=C09679609679583C /dos            ntfs    defaults,umask=007,gid=46 0       0
/dev/sda1       none            swap    sw              0       0

```

---

### Post by garvinrick4 on 2011-01-19
I believe it says during installation it was there. If it is not there get rid of it.
Make a copy of fstab, delete offending lines and save. Reboot and see if all
is well. If anything funny happens reinstall the saved fstab.
You say it is deleted.
What does this say is there.
```
sudo fdisk -l
``` (lower case L)

---

### Post by axept on 2011-01-19
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a2f9ac4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275        1288      102400   83  Linux
/dev/sda3            1288       42985   334925824   83  Linux
/dev/sda4           42985       60802   143116288    7  HPFS/NTFS

```


My point, I deleted /sda2 becasue it was the hidden partition to win7. After I formated the HDD and did a clean install of Ubuntu, grub still saw that partition. So I formated that partition /sda2 to ext4 afterwards. I think its the reason. Can I just delete the line in fstab about that /dos thing ? :P

---

### Post by garvinrick4 on 2011-01-19
##Go ahead and delete that line in your fstab.
sda2 looks like a /boot partition 
sda3 looks like / in linux
sda4 is a NTFS partition which linux can read fine.
sda1 is some sort of what recovery tools type partition is it a Dell or something.
fstab shows swap there at one time.
#If you want to see what each one represents. Download this to desktop; Make sure it
is to desktop.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
# After downloaded open terminal and run this:
```
sudo bash ~/Desktop/boot_info_script*.sh 
```
# Will put a file on Desktop that says RESULTS will have all the info
in there, Copy and paste here and it will be read for you.

---

### Post by axept on 2011-01-19
Well, I deleted the line in fstab, and maked a new one:

```
/dev/sda2       /Extra          ext4    rw              0       0   
```

Now it was no problem at start-up and it got auto mounted without any problems.

sda1 is kind of a strange thing, its a acer aspire. I dont know about that one, anyway it doesn't matter to me :)

Thanks for the help!

---

