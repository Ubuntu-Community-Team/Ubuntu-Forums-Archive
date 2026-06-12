---
title: "huge hard drive mess"
date: 2010-05-26
forum: General Help
---

### Post by mishypie on 2010-05-26
So basically, as rookie as it sounds, i spent about 3 days trying to figure out why my computer wouldn't boot (BIOS not found, then it ran grub rescue) until i saw that my external hard drive (which evidently somehow has some file on) was unplugged. duh. 

Im running windows and ubuntu 10.4 on partitions on my computer's internal 120gb drive.

The problem I have is that during these 3 days, i re-installed ubuntu on the drive from the CD- so i think I have 3 partitions, even though the 3rd does not show up as an option to boot into from startup. What it does show though, is on my desktop I have 2 mounted drives:

one 52gb one that has my Windows files in it, and one 44gb one that has ubuntu files in it, but NOT the ones i use- this is the rogue copy i installed by "accident". i checked this by looking through the contents and it was all minimal (nothing in home folder)

My question is, how do i "remove" this partition safely, and return to having just a windows an ubuntu partition?

many thanks, sorry for long and fairly unclear post!

---

### Post by ajgreeny on 2010-05-26
You have lost me somewhat!

Do you have ubuntu on the external disk as well as the internal drive, and if so which is the version you really wish, or need, to keep.

Just to be sure what is going on can you please attach your external drive and then run ```
sudo fdisk -l
``` in terminal and report the output back here.

It will also be useful to download and run the **boot-info-script** from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) and then post back the RESULTS.txt file that you should find in the folder from which you run the script.  That will give a lot more info about grub and your boot setup.

You can do all of this from the Live CD if you can not get into your installed ubuntu.

---

### Post by mishypie on 2010-05-26
> **ajgreeny said:**
> You have lost me somewhat!

Do you have ubuntu on the external disk as well as the internal drive, and if so which is the version you really wish, or need, to keep.

Just to be sure what is going on can you please attach your external drive and then run ```
sudo fdisk -l
``` in terminal and report the output back here.

It will also be useful to download and run the **boot-info-script** from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) and then post back the RESULTS.txt file that you should find in the folder from which you run the script.  That will give a lot more info about grub and your boot setup.

You can do all of this from the Live CD if you can not get into your installed ubuntu.

The thing that confused me was I have nothing system-wise on my external, only music, games ect, however, as my computer failed to boot without it, something must be on it that is required.

I ran sudo fdisk -l and got

```
 Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9e6a9e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6280    50437928    7  HPFS/NTFS
/dev/sda2            9051       14594    44520449    5  Extended
/dev/sda5            9051       14361    42651648   83  Linux
/dev/sda6           14361       14594     1867776   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d015d38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37512   301308802+   7  HPFS/NTFS
/dev/sdb2           37512       60802   187077633    5  Extended
/dev/sdb5           37512       60428   184074240   83  Linux
/dev/sdb6           60428       60802     3002368   82  Linux swap / Solaris

```

I am currently in the partition of Ubuntu that I use normally, so thats not a problem, just the extra partition I accidently installed when trying to figure out what was going on.

I downloaded the boot info script but when I got ```
 misha@mishas-computer:~$ sudo bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory 
```

Any help appreciated. Thanks.

---

### Post by ajgreeny on 2010-05-26
You will have to run this file as root.

---

### Post by wilee-nilee on 2010-05-26
The script is easy to run once you understand it you left out the location. Use a live cd since your setup is borked, download it drag it on to the desktop and run.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

