---
title: "Cannot Change Permission For FAT Partition Even After Using Sudo."
date: 2010-08-22
forum: General Help
---

### Post by satyanash on 2010-08-22
Hi,
   So my computer has 512 MB of ram. so it's slow. The Lucid 10.04 Desktop version was too slow for me and installing the LXDE environment did not increase the performance much.. so i what i did was that i installed Ubuntu Server Lucid 10.04 64-Bit, and then on top of that installed the lxde environment.. So by default i don't have nautilus, but i have the PCman File manager. So heres the problem :

1 I dual boot windows XP and Ubuntu server lucid 64 bit NOW.

2 I have two FAT32 partitions that i use for Data storage, and thus they can be natively read by both OS.

3 In my earlier Ubuntu Lucid Desktop the two partitions would be automatically mounted and displayed at the desktop, and i was able to access them with ease.

4 Now they are not automatically mounted, and when i mount them through the command line i can only access them using sudo. I cannot access them at all through GUI(PCMan File Manager).

5 When i check permissions the owner is root and nobody has any other permissions (drwx------).

6 Now i tried to change the owner using sudo through chown, it doesnt show any error and it seems like it has been successful, but when i check it again there is no effect.

7 Then i try changing the permissions as root and chmod, this time i get an error like cannot change permissions: Operation not permitted. (This is strange since i am root)

8 Then just to make sure i tried the obove two commands with sudo -i and sudo -s but with same results.

9 Then i thought of checking the fstab: 

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=95d48af1-7b4c-4d6f-ac75-cac02ba7b009 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a510c050-9f4b-4f5e-84e3-1265d8a6dbd8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

This was when i also noticed the errors=remount-ro.
But i don't think my linux partition is in read only mode.. I know my hard disk has some bad sectors(only 2 actually), but i can confirm that my linux root partition is not remounted as read only because i was able to create folders and etc.

10 And for a better idea here is my fdisk -l :

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4f2f4f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        3825    15357952    b  W95 FAT32
/dev/sda3   *        3825        6256    19530752   83  Linux
/dev/sda4            6256        9730    27901953    5  Extended
/dev/sda5            6256        6381      999424   82  Linux swap / Solaris
/dev/sda6            6381        9730    26901504    b  W95 FAT32

```

So what i want is: Access through the GUI and maybe automount cuz it contains all my music, photos et cetera and also my windows Save Games.

Oh and BTW now my Ubuntu runs with a considerably good speed, only need to get this problem solved.

Satyajeet

---

### Post by darolu on 2010-08-22
You need to add entries to your fstab file for your FAT32 file systems.
For example, your sda6 one:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=95d48af1-7b4c-4d6f-ac75-cac02ba7b009 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a510c050-9f4b-4f5e-84e3-1265d8a6dbd8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[b] # FAT32 Partition on /dev/sda6
/dev/sda6        /media/<mydisk>  vfat    defaults    0    0[/b]
```
You will need to create a mount point inside /media and change <mydisk> for whatever you have chosen, for example:
```
sudo mkdir /media/mydisk
```

---

### Post by satyanash on 2010-08-22
Okay but Will this also solve the permissions problem ?

---

### Post by QLee on 2010-08-22
> **sattu94@gmail.com said:**
> Okay but Will this also solve the permissions problem ?

These might help to explain it.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ownership and permissions of vfat / ntfs are set at the time of mounting. 
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by satyanash on 2010-08-22
Thanks for the FSTAB edits Darolu, and also for the links, QLee They all helped i finally got those partitions up and working..yay !!!
Thanks a lot. Anyway Does ubuntu desktop does all of this automatically ?

---

### Post by QLee on 2010-08-22
[QUOTE=sattu94@gmail.com]... Anyway Does ubuntu desktop does all of this automatically ?[/QUOTE]

As long as you have not used the option, "noauto" in the line you entered into your fstab, yes.
Fstab is parsed at boot time and filesystems described there are mounted. 

If you want the stuff you write in fstab to take effect right after you save it, you can issue the command, mount -a, in a terminal.

---

