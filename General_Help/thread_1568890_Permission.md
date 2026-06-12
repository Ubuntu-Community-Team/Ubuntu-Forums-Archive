---
title: "Permission"
date: 2010-09-06
forum: General Help
---

### Post by octohedra on 2010-09-06
Hello,

I dont have permissions of my partitions, i have like 5 partitions, and cant write in any of them, so i cant use transmission :(
Is there any way to fix this? 

thanks!

---

### Post by octohedra on 2010-09-06
fixed it with gksudo nautilus, but i dont want to be vulnerable to attacks, is there any other way?

---

### Post by Ghost_Mazal on 2010-09-06
Are they NTFS or EXT partitions ? If they are EXT you can consider creating mount points for them and give your userid the neccesary permissions to the mounted folders.

---

### Post by octohedra on 2010-09-06
how do i do that? i mean with that procedure ill be able to write/read with any program without having to be typing my password every time, but if anyone tries to write/read my data will be asked for a password?

Thanks! ):P

---

### Post by deserthowler on 2010-09-06
> **octohedra said:**
> 

I dont have permissions of my partitions,
Is there any way to fix this? 

thanks!

look at chmod in the man pages

Earl

---

### Post by octohedra on 2010-09-06
> **deserthowler said:**
> look at chmod in the man pages

Earl
man i just ***** up my computer, in the terminal i run the command: sudo chmod 774 / and the terminal closed, lost my desktop and everything, and couldnt open the terminal again, so reset the computer and i get a BLACK screen and cant do absolutely nothing.

Now im booting from slitaz, 

please need some advice :( :(  how do i get my ubuntu 10.04  installation working again? I tried booting from the ubuntu cd, and i opened the termnal, run the command sudo chmod 777 / but NOTHING :(

what can i do?

---

### Post by octohedra on 2010-09-06
please im waiting for an answer so i can get my computer working again... :popcorn:

---

### Post by printfw on 2010-09-06
By chmod you made a mess with system permissions. I think the fastest way to get a working computer is to reinstall OS. And for the future, partition permissions is set by editing */etc/fstab*.

---

### Post by sandyd on 2010-09-06
> **octohedra said:**
> man i just ***** up my computer, in the terminal i run the command: sudo chmod 774 / and the terminal closed, lost my desktop and everything, and couldnt open the terminal again, so reset the computer and i get a BLACK screen and cant do absolutely nothing.

Now im booting from slitaz, 

please need some advice :( :(  how do i get my ubuntu 10.04  installation working again? I tried booting from the ubuntu cd, and i opened the termnal, run the command sudo chmod 777 / but NOTHING :(

what can i do?
reinstall. then
post the output of
```

cat /etc/fstab
sudo fdisk -l
```

---

### Post by octohedra on 2010-09-06
Well, i was trying to install it instead of the other installation i had before, but it wouldnt let me due to some partition problem, so i selected the "install next to previous installation and select it when booting". Everything working fine now, but i think i lost all my previous installs, like WINE for example.

Also i had some downloads in my user folder, and during install it asked me if i wanted to copy them to this intall and i slected them for that, but i cant find them, where are them?

So, what i need is to: 

Delete the previous install.
Get all my soft again.
Updates.
Recover my data from the last install.


Thanks! ):P

---

### Post by sandyd on 2010-09-06
> **octohedra said:**
> Well, i was trying to install it instead of the other installation i had before, but it wouldnt let me due to some partition problem, so i selected the "install next to previous installation and select it when booting". Everything working fine now, but i think i lost all my previous installs, like WINE for example.

Also i had some downloads in my user folder, and during install it asked me if i wanted to copy them to this intall and i slected them for that, but i cant find them, where are them?

So, what i need is to: 

Delete the previous install.
Get all my soft again.
Updates.
Recover my data from the last install.


Thanks! ):P
post the output of
```

cat /etc/fstab
sudo fdisk -l
```

---

### Post by octohedra on 2010-09-06
mrfunky@AMDxUbuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=97870155-9d20-4184-a08d-f36f8c92c22a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=8fec094f-1454-46c7-869e-3553c99060ea none            swap    sw              0       0
mrfunky@AMDxUbuntu:~$ sudo fdisk -l
[sudo] password for mrfunky: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000772d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97654784   83  Linux
/dev/sda2           12158       60801   390727201+   5  Extended
/dev/sda5           12158       12413     2050590+  82  Linux swap / Solaris
/dev/sda6           12414       17512    40957686   83  Linux
/dev/sda7           17513       23886    51199123+  83  Linux
/dev/sda8           23887       33446    76790216+  83  Linux
/dev/sda9           43009       60801   142922241   83  Linux
/dev/sda10          33446       42613    73632768   83  Linux
/dev/sda11          42613       43008     3173376   82  Linux swap / Solaris

Partition table entries are not in disk order

my pendrive:

Disk /dev/sdb: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf4abf4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7840     2007024    b  W95 FAT32
mrfunky@AMDxUbuntu:~$

---

### Post by octohedra on 2010-09-06
Any words of advice? I want to be able to read/write in all those partitions...

Thanks.

---

### Post by octohedra on 2010-09-07
bump

---

### Post by printfw on 2010-09-07
Add in */etc/fstab* something like that for any partition you want to be mount:
```
/dev/sda6  /mnt/where_to_mount               ext4  defaults                     0  0
```
More of that you can find in *man fstab*. 
Or just install **pysdm** package. It is graphical tool for partition management.

---

### Post by octohedra on 2010-09-07
> **printfw said:**
> Add in */etc/fstab* something like that for any partition you want to be mount:
```
/dev/sda6  /mnt/where_to_mount               ext4  defaults                     0  0
```More of that you can find in *man fstab*. 
Or just install **pysdm** package. It is graphical tool for partition management.

Thanks ! ):P

So i "copy that code and paste it" in the terminal and i'll be able to rw in all my partitions?

Something very weird is that before re-installing ubuntu i had only 6 sda, now i have 11 sda :o

I need some advice on how to uninstall previous ubuntu succesfully without messing up drivers, permissions etc...

I want to be able to move something from the desktop for example to any of my hd partitions, i dont mind typing a password, but it wont even let me do that, just "Permission denied" or execute files, etc..

Thanks again,

Octohedra

---

### Post by printfw on 2010-09-07
> **octohedra said:**
> Thanks ! ):P

So i "copy that code and paste it" in the terminal and i'll be able to rw in all my partitions?
Not exactly. You need to add such a line to */etc/fstab* with proper correction for your system, replacing */dev/sda6*(partition),  */mnt/where_to_mount* and *ext3*(filesystem type) with yours. Anyway, as I said the easiest way to do that is installing **pysdm** package.

> **octohedra said:**
> I want to be able to move something from the desktop for example to any of my hd partitions, i dont mind typing a password, but it wont even let me do that, just "Permission denied" or execute files, etc..

Thanks again,

Octohedra
After mounting all filesystems needed, change the owner of mountpoint, **not root directory**:
```
sudo chown -R your_username /mnt/where_to_mount
```
and you will be able to rw to that partition.

---

### Post by octohedra on 2010-09-07
Seems to be something that will take me some time to work it out, i dont want to **** up my machine agian, anyways, i would like if its not much bother, that someone give me some pointers in this:

How to uninstall previous ubuntu installation without loss of data/drivers/permissions/etc.

Also if its not too bothersome, could you please be a little bit more specific with the instructions? im scared of doing something wrong and having to start all over from 0 again... i hope you dont mind guiding me a bit more through the process... 
I would like to be able to rw to my partitions but directly to them, otherwise i would have to open my /mnt/$partition_name$ and do it from there ? If its possible i would like to access & rw just opening them directly? or its the same?

):P

---

### Post by oldos2er on 2010-09-07
> **octohedra said:**
> How to uninstall previous ubuntu installation without loss of data/drivers/permissions/etc.


Don't really understand the question. If you uninstall something, it's (usually) gone. Uninstalling without loss of data is oxymoronic. 

Some info on *nix permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[http://linux.about.com/od/ubuntu_doc/a/ubudg24t3.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t3.htm)

[http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html)

---

### Post by octohedra on 2010-09-08
I know it sounds kind of dumb, but im just starting with this, how do i make sure im uninstalling the old installation and not the current? They have the same name  :p 
And how do i make sure i wont lose my drivers and newly aquired software...? Maybe its useless to worry about this, but as i said im new, and i dont want to **** it up again... 
Last time i tried partitioning my hd i made a 400gb swap partition, then **** up the permissions and had to re-install everything again... lol

Thanks for the links oldos2er, im studying it and its very helpful.

):P

---

### Post by oldos2er on 2010-09-08
Let's take a look at your partitions, if you don't mind. Can you run ```
sudo fdisk -l
``` in a terminal, and post the output here?

In Synaptic Package Manager, under File, Save Markings, you can create a list of all installed packages, and then use that to install the same packages to a fresh Ubuntu install. More about that here: [http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html](http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html)

---

### Post by octohedra on 2010-09-08
Hi oldos2er, thanks for helping me out!

Here's what you requested:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000772d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97654784   83  Linux
/dev/sda2           12158       60801   390727201+   5  Extended
/dev/sda5           12158       12413     2050590+  82  Linux swap / Solaris
/dev/sda6           12414       17512    40957686   83  Linux
/dev/sda7           17513       23886    51199123+  83  Linux
/dev/sda8           23887       33446    76790216+  83  Linux
/dev/sda9           43009       60801   142922241   83  Linux
/dev/sda10          33446       42613    73632768   83  Linux
/dev/sda11          42613       43008     3173376   82  Linux swap / Solaris

Partition table entries are not in disk order

):P

---

### Post by oldos2er on 2010-09-08
A lot of Linux partitions! If you post the output from ```
sudo blkid
``` and ```
cat /etc/fstab
``` I can help you figure out which partition(s) you'll need to keep (assuming it's the one you're currently booted from).

---

### Post by doramider7 on 2010-09-09
how do i do that? i mean with that procedure ill be able to write/read with any program without having to be typing my password every time, but if anyone tries to write/read my data will be asked for a password?

Thanks! ):P

---

### Post by octohedra on 2010-09-09
> **oldos2er said:**
> A lot of Linux partitions! If you post the output from ```
sudo blkid
``` and ```
cat /etc/fstab
``` I can help you figure out which partition(s) you'll need to keep (assuming it's the one you're currently booted from).

```
sudo blkid
[sudo] password for user: 
/dev/sda1: UUID="716360a0-1a32-45c8-a9a0-6898a7d4eef5" TYPE="ext4" 
/dev/sda5: UUID="7c16a1f5-7624-41f0-aad9-437c1d869509" TYPE="swap" 
/dev/sda6: LABEL="Part-2" UUID="73e29bb0-19df-45e4-ac9c-ea62e592acc5" TYPE="ext4" 
/dev/sda7: LABEL="Part-3" UUID="70dc5dd7-913f-423f-a49c-3cf215906894" TYPE="ext3" 
/dev/sda8: LABEL="Part-4" UUID="0993560e-053d-46cf-8ba3-18e8c16faa2c" TYPE="ext3" 
/dev/sda9: LABEL="Part-5" UUID="7b32c61a-9466-47d7-bade-c2ab38395580" TYPE="ext3" 
/dev/sda10: UUID="97870155-9d20-4184-a08d-f36f8c92c22a" TYPE="ext4" 
/dev/sda11: UUID="8fec094f-1454-46c7-869e-3553c99060ea" TYPE="swap" 

``````
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=97870155-9d20-4184-a08d-f36f8c92c22a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=8fec094f-1454-46c7-869e-3553c99060ea none            swap    sw              0       0

```

---

### Post by octohedra on 2010-09-11
Bump

---

### Post by octohedra on 2010-09-13
> **octohedra said:**
> Bump

:popcorn:

---

### Post by octohedra on 2010-09-16
alright i get it, im a noob... still need some help with this... :oops:

---

### Post by printfw on 2010-09-16
According *blkid* output and */etc/fstab* your current system is installed on */dev/sda10* using */dev/sda11* as swap.

---

