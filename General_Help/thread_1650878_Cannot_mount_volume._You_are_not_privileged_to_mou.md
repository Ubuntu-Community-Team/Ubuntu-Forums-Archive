---
title: "Cannot mount volume. You are not privileged to mount the volume 'DATA'."
date: 2010-12-22
forum: General Help
---

### Post by Jammanuser on 2010-12-22
Hello,
I am having a problem in Ubuntu 8.10. A while back I manually added a partition to be mounted automatically at boottime to my fstab file, and it worked fine for a long time. Now, however, for some reason, I'm getting a message when Ubuntu loads up, which says the following:

> 
Cannot mount partition.

You are not privileged to mount the volume 'DATA'.

I don't understand why it would be saying this now, after it was able to mount it countless times before, and I made no changes (except for copying files over to the partition from Ubuntu) to the partition or fstab since.

Here is my sudo fdisk -l info:

> 
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c5a8d58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               6        1279    10233405    7  HPFS/NTFS
/dev/sda3           19765       34361   117250402+   f  W95 Ext'd (LBA)
/dev/sda4   *       17216       19764    20474842+  83  Linux
/dev/sda5           19765       20337     4602591   82  Linux swap / Solaris
/dev/sda6           20338       27986    61440561    7  HPFS/NTFS
/dev/sda7           27987       34361    51207156    7  HPFS/NTFS

Partition table entries are not in disk order

I believe /dev/sda6 is my 'DATA' volume/partition. As you can see it is an logical NTFS partition inside the extended /dev/sda3 partition.

And here is my /etc/fstab file's contents:

> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0

# /dev/sda1
UUID=4EF4BF01F4BEE9FB     /media/sda1     ntfs-3g       defaults         0   0

# /dev/sda2
UUID=74D4CA25D4C9E986     /media/sda2    ntfs-3g        defaults         0   0

# /dev/sda3
UUID=2C6EDB496EDB0B0A       /media/drv0       ntfs-3g         defaults      0   0

# /dev/sda4
UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5     /               ext3        defaults,errors=remount-ro    0   1

# /dev/sda5
UUID=94cd6bbb-4b8c-437e-abef-fb744053d906      none            swap        sw          0   0

# /dev/sda6
UUID=162839AD28398D2D   /media/DATA    ntfs-3g   defaults      0    0

# /dev/sda7
UUID=786CF89A6CF853FA   /media/sda7   ntfs-3g    defaults      0    0


Thanks in advance for any help.

-Jam Man

:guitar:

---

### Post by dino99 on 2010-12-22
few things:

- have /etc/fstab with sda4 & sda5 only (your boot & swap partitions)

- sudo blkid ( to check uuids and compare with the fstab ones)

you can install mountmanager to deal with all your devices & partitions rights. Check (into synaptic), that mountall, ntfsprogs, ntfs-3g are installed.

---

### Post by dabl on 2010-12-22
> **Jammanuser said:**
> 

 I made no changes (except for copying files over to the partition from Ubuntu)



Did you perchance use "sudo" to copy the files -- did you copy them with root permissions?  That would be a no-no, and might lock your user out of the directory.

---

### Post by Jammanuser on 2010-12-22
> **dino99 said:**
> few things:

- have /etc/fstab with sda4 & sda5 only (your boot & swap partitions)

Well, the thing is, I want to be able to access the other partitions listed in /etc/fstab also, as soon as Ubuntu loads. If I have to mount the other partitions manually through the command-line first, that would be a pain.
> 
- sudo blkid ( to check uuids and compare with the fstab ones)

```

/dev/sda4: UUID="dd4f326a-2165-40f6-aed4-2b44b15b71a5" TYPE="ext3" LABEL="Ubuntu-real" 
/dev/sda6: UUID="162839AD28398D2D" LABEL="DATA" TYPE="ntfs" 
/dev/sda7: UUID="786CF89A6CF853FA" LABEL="Programs" TYPE="ntfs" 
/dev/sda2: UUID="74D4CA25D4C9E986" LABEL="Recovery" TYPE="ntfs" 
/dev/sdb1: LABEL="SA-20G IPOD" UUID="3141-5926" TYPE="vfat" 
/dev/sda1: UUID="4EF4BF01F4BEE9FB" LABEL="WINXP-OS" TYPE="ntfs" 

```
> 
you can install mountmanager to deal with all your devices & partitions rights. Check (into synaptic), that mountall, ntfsprogs, ntfs-3g are installed.
Attempting to "sudo apt-get install mountmanager" produced the following messages in my Terminal:

> 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Why would it be saying that?
I looked in Synaptic, and searched for the titles you mentioned, and learned the following:

1. No package called "mountall" could be found.
2. ntfsprogs was not installed yet, but showed up in the package list, so I went ahead and installed it.
3. ntfs-3g was already installed.

Thanks for the reply.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2010-12-22
> **dabl said:**
> Did you perchance use "sudo" to copy the files -- did you copy them with root permissions?  That would be a no-no, and might lock your user out of the directory.
Crap..
Yeah, I may have. I seem to vaguely recall sudo cp-ing something over to the partition 'DATA' from Ubuntu's partition (/dev/sda4) at some point right before I noticed that I couldn't mount the partition anymore, possibly because it wouldn't let me copy the file over using the GUI because of the file's permissions, but I'm not sure if I did that or not.
Perchance I did do that...what can I do now to fix that problem? :)

Thanks for the reply.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2010-12-22
> **Jammanuser said:**
> 
Attempting to "sudo apt-get install mountmanager" produced the following messages in my Terminal:


Why would it be saying that?

Nevermind. Figured it out. It was because Synaptic was open when I ran that command. Once I closed it, I no longer got that message. However, I still was unable to install it. Here's the terminal output now:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libraw1394-dev libavutil-dev libdc1394-22-dev
  linux-headers-2.6.27-16-generic libtheora-dev
  linux-headers-2.6.27-11-generic linux-headers-2.6.27-11
  linux-headers-2.6.27-14 linux-headers-2.6.27-15 linux-headers-2.6.27-16
  linux-headers-2.6.27-14-generic ocaml-base-nox
  linux-headers-2.6.27-15-generic libgsm1-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mountmanager
0 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
Need to get 500kB of archives.
After this operation, 1855kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  mountmanager
Install these packages without verification [y/N]? y
[B]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe mountmanager 0.2.4-0ubuntu1
  404 Not Found [IP: 91.189.92.170 80][/B]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mountmanager/mountmanager_0.2.4-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mountmanager/mountmanager_0.2.4-0ubuntu1_amd64.deb)  404 Not Found [IP: 91.189.92.170 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Attempting to install from Synaptic produced a similar 404 Not Found message.
It seems the file doesn't exist on the server anymore?

---

### Post by dabl on 2010-12-23
> **Jammanuser said:**
> ```

```

Perchance I did do that...what can I do now to fix that problem? :)



```
sudo chown jam:jam /mnt/wherever/data/file
```

take a look at

```
man chown
``` for more.

---

### Post by Jammanuser on 2010-12-23
> **dabl said:**
> ```
sudo chown jam:jam /mnt/wherever/data/file
```

take a look at

```
man chown
``` for more.
Interesting...
First time I've heard of the program chown.
Could I use it on the whole partition instead of just an individual file?
BTW, I looked in the manual, and couldn't find any reference for the option "jam:jam" or even "jam" for that matter.

---

### Post by Jammanuser on 2010-12-23
Hmm...I just tried to mount the DATA partition manually through the command line, and here is the terminal output:

> 
gorilla@ubuntu:~$ sudo mount /dev/sda6 /media/DATA
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 /media/DATA -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 /media/DATA ntfs-3g force 0 0

I think instead of forcing the mount, I'm going to go try to run a chkdsk on the partition from XP. I'll let y'all know how it goes.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2010-12-23
Running chkdsk on the partition solved the problem. :popcorn:
The partition DATA is now automatically mounted once again when Ubuntu loads, and I was able to copy over the folder and its contents that I was needing to copy to it, and everything's working fine now.

Thanks guys.

Cheers.

-Jam Man

:guitar:

---

