---
title: "Target Filesystem doesn't have /sbin/init. (Can't boot)"
date: 2011-04-06
forum: General Help
---

### Post by sdude on 2011-04-06
Click here for solution... [http://ubuntuforums.org/showpost.php?p=10646699&postcount=3]("http://ubuntuforums.org/showpost.php?p=10646699&postcount=3")

So I just realized how stupid I was being trying to run these commands for a NTFS partition... so I searched and used Gparted to check sda2, and also ran 

```
root@ubuntu:/home/ubuntu# sudo ntfsfix /dev/sda2
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed successfully.
root@ubuntu:/home/ubuntu# 
```

but with no luck im still not able to boot... 

So... this evening I tried to boot ubuntu as per usual.. (everything was fine until today)...And I end  up getting GRUB reporting this to me..

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target Filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_
```

Now ive searched and searched and most people have found solutions to this using a live CD and running e2fsck or fsck but heres my problem..

This is my...fdisk -l for /dev/sda

```


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xedb699b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2089    16777216   27  **Unknown**
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2089       20254   145905664    7  HPFS/NTFS
/dev/sda3           20254       38913   149884749    7  HPFS/NTFS

```

As you can see SDA2 is NTFS not linux I think this is where I installed ubuntu within windows without a separate partition.

[B]I probably shouldnt have done but I searched this up and tried every fsck and e2fsck command I could see people suggesting .. and all failed (probably because I have no idea what these commands do! :S....Im pritty sure these commands only work for standard filesystems as mines NTFS I think this is why im getting the (@The superblock could not be read or does not describe a correct ext2 filesystem.@)
[/B]

Heres my guess my OS was installed using a .iso from the ubuntu website 10.10 I mounted the image and installed within windows as to not mess around with partitions had no problems what so ever been using ubuntu for about a week now... last thing I remember doing was trying to mount my data drive (with world of warcraft on it) so that I could read and write.. as it was a NTFS partition it wasnt having any of it , so I messed around in fstab but that didnt work so I removed what I put at the bottom... and eventually got it working with ntfs-config on the ubuntu help...  as the program was windows I had to chroot the .exe to +X (as it was running via the latest wine) but as it was ntfs it wouldnt let me , but as I said I got this working with ntfs-config...

so... from the top I think I may have busted the fstab (perhaps) this data drive is actually a partition on the same drive as the system drive I only have one NTFS HDD in my pc... so perhaps messing around with the ntfs-config has messed up the boot I dont know...

so ive tried lots of different e2fsck or fsck commands but I end up with things like this...

```
root@ubuntu:/home/ubuntu# fsck -y /dev/sda1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
root@ubuntu:/home/ubuntu# fsck -y /dev/sda2
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2
root@ubuntu:/home/ubuntu# fsck -y /dev/sda3
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda3

```


Now trying some different fsck commands I ended up with this..

```
root@ubuntu:/home/ubuntu# e2fsck -b 8193 /dev/sda2
e2fsck 1.41.12 (17-May-2010)
/dev/sda2 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? yes

e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

``` 

That was with it mounted for some reason it was mounted, so I proceeded to unmount it and I just got the same error upon re-trying the command

```
root@ubuntu:/home/ubuntu# e2fsck -b 8193 /dev/sda2
e2fsck 1.41.12 (17-May-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

[COLOR="Red"]**EDIT!: **[/COLOR]
1. Ive realised sda2 is where the linux is because when I mounted (ACER: ) it has the windows on it, and thats where ubuntu is stored too on the root of that drive I think... and when I ran  e2fsck -b 8193 /dev/sda2 it said its mounted (because it was)... so SDA2 is windows + ubuntu Sda1 have no idea some PQservice or somthing, and sda3 is my other partition which is (DATA: ) and then I thought about opening the disc utility and that practically showed me exactly what was what.

[[IMG]http://img534.imageshack.us/img534/8868/screenshotpe.png[/IMG]](http://img534.imageshack.us/i/screenshotpe.png/)

2.I'm pritty sure that this isnt meant to be listed like this too as I fdisk -l after it shows the bit quoted at the start with the UNKNOWN sda1 it shows this...

```

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      799843      861054   123339962   f4  SpeedStor
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(793, 22, 13) logical=(799842, 56, 21)
Partition 1 has different physical/logical endings:
     phys=(870, 235, 61) logical=(861053, 49, 48)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       93845      176285   166116794   10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(93844, 22, 54)
Partition 2 has different physical/logical endings:
     phys=(870, 235, 50) logical=(176284, 29, 7)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?       55982       55982           5   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(367, 66, 47) logical=(55981, 0, 13)
Partition 3 has different physical/logical endings:
     phys=(370, 32, 37) logical=(55981, 0, 22)
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order

```


[B]Can someone please help me restore my boot, I miss my ubuntu :(!

Many thanks,[/B]
Scott.

---

### Post by techunit on 2011-04-06
You can see all of your kernel images in Grub right? You should be able to select another one and see if that helps.

On the worse end you might need to boot into a live cd move over your documents and try agian with a clean install.

Most of my success has been with fixing grub problems in dualboots after they break windows or Ubuntu's boot. You had so much information I'll have to look it over.

---

### Post by sdude on 2011-04-06
**[COLOR="Red"]So I managed to fix it!!! [/COLOR]**

As my system was installed inside windows (without a sperate partition it became apparent it would be tricky to fix the boot as the check commands only work on ex2 file systems I believe.... 

You will need to create a folder and mount your windows partition on before you can get access to the file... 

I cant tell exactly how I did it because the conversation window open was online messenger... somthing along the lines of mounting sda2 (The windows and linux partition) and locating the system in my case **(C:/ubuntu/disks/root.disk)** I just ran (after cd'ing into the directory)...

```

sudo su

e2fsck -p ./root.disk

then that seemed to work, but I forced it as well just incase using...

e2fsck -f ./root.disk

and answered yes carefully to everything


```

rebooted and it worked :)

---

