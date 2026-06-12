---
title: "Ubuntu's disk space problem"
date: 2011-09-07
forum: General Help
---

### Post by latvian on 2011-09-07
Hello,

I have installed Ubuntu 11.04 on a dual boot system, alongside Windows 7. I have created 2 partition, one is 150 GB for Windows and the other one is 450 for Ubuntu. Downloaded the Windows Ubuntu Installer on the larger partition and started the installation process. Now I am using Ubuntu and every time I copy a rather large file from my external hard disk to Ubuntu's Desktop, I got an error that there is no disk space although, as I mentioned above, I have created a very large partition for Ubuntu and it's almost free. 

How can I fix that?

Thanks in advance...

---

### Post by coffeecat on 2011-09-07
> **latvian said:**
> Downloaded the Windows Ubuntu Installer on the larger partition and started the installation process.

That's the wubi installer. It doesn't matter how large the partition is, if you use wubi, your installation size is limited to the size of the root.disk file, which is the wubi Ubuntu pseudo-partition. The size is set in the first window of the installer and the default size is only 8GB. If you had wanted Ubuntu to take up 450GB you would have needed to boot from a live CD or live USB prepared from an Ubuntu ISO and run the installer to create an Ubuntu installation with its own filesystem.

However, a 450GB Ubuntu partition is not a good use of the hard drive space you have there. Apart from the fact that Ubuntu uses a separate swap partition, if you were setting up a conventional dual-boot with Windows, it would be better to have an Ubuntu root partition of only about 20-30GB and then another large partition for storing personal data which can be accessible from both Windows and Ubuntu.

In the meantime, so that we can see what your system is like now, open a terminal and post the output of these commands:

```
sudo fdisk -lu
df -h
mount
```

---

### Post by latvian on 2011-09-07
> **coffeecat said:**
> 

In the meantime, so that we can see what your system is like now, open a terminal and post the output of these commands:

```
sudo fdisk -lu
df -h
mount
```
```

sudo fdisk -lu


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xdf35d666

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2         3074048   317653244   157289598+   7  HPFS/NTFS
/dev/sda3      1221351424  1250263039    14455808   17  Hidden HPFS/NTFS
/dev/sda4       317653245  1221341624   451844190    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       317653308  1221341624   451844158+   7  HPFS/NTFS
Partition 5 does not start on physical sector boundary.

Partition table entries are not in disk order

``````

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   13G  2.4G  85% /
none                  2.9G  692K  2.9G   1% /dev
none                  2.9G  352K  2.9G   1% /dev/shm
none                  2.9G  252K  2.9G   1% /var/run
none                  2.9G     0  2.9G   0% /var/lock
/dev/sda5             431G   18G  414G   5% /host

``````

/dev/loop0 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda5 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ammar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ammar)

```

---

### Post by coffeecat on 2011-09-07
Your sda5 partition is formatted NTFS and is 462.7GB in size = 430.9 GiB (gibibytes). Your wubi root.disk is in your sda5 partition and is approx 17GB (or approx 16GiB) in size, and is 85% full.

Have a look at the wiki page for wubi:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Under 8-8 and 8-9 are guides for migrating a wubi install to its own partition and resizing the wubi virtual disk respectively. Neither are particularly straightforward.

Your alternative is to create a conventional installation by shrinking sda5 and creating more logical partitions for Ubuntu. You need to know a bit about partitioning for this, and this is a good guide:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

And for that you would need a live CD of Ubuntu for both the Gparted partition editor and the installer. See:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by al1x on 2011-09-07
> it would be better to have an Ubuntu root partition of only about 20-30GB and then another large partition for storing personal data which can be accessible from both Windows and Ubuntu.

As far as I know, I can have access to Windows partitions when I'am running Ubuntu but not the other way round.So, you suggest to have a filesystem partition for Ubuntu and mount every time the other partition(for both win and ubuntu)with the personal files,movies,games etc.?Or, maybe, there is a more efficient way to do this?

---

### Post by coffeecat on 2011-09-07
> **al1x said:**
> As far as I know, I can have access to Windows partitions when I'am running Ubuntu but not the other way round.So, you suggest to have a filesystem partition for Ubuntu and mount every time the other partition(for both win and ubuntu)with the personal files,movies,games etc.?Or, maybe, there is a more efficient way to do this?

Repeatedly mounting the Windows C: partition from Ubuntu is not a good idea - in my opinion. I think you'll find that opinion shared widely. It's too easy to accidentally delete or damage important system files on the Windows partition. Just as Windows knows nothing about Linux permissions, so Linux does not respect Windows permissions. I prefer to have a separate NTFS partition solely for data with a Windows/Ubuntu dual-boot. This is easily mounted in Ubuntu and will be seen as D: or E: or whatever by Windows.

---

### Post by al1x on 2011-09-07
Okay, now I see, thanks for the advice! :)

---

### Post by al1x on 2011-09-07
Ehmm...Is there any way to have this shared partition mounted automatically when you log in ubuntu?

---

### Post by MG&amp;TL on 2011-09-07
Step 1. Find the mount command. (I don't know specifically how to do this, look it up on the web, and supply your own values)

Step 2. Open "startup applications", and add a value in there with the terminal command from step 1. Reboot, and I think you're done.

Correct me, please CoffeeCat. :)

---

### Post by jerome1232 on 2011-09-07
That's not the ideal way, you would want to add it to your fstab, a file which lists the partitions and where they are to be mounted at during startup.

There are some nice easy to use gui's for this, have a read here

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by MG&amp;TL on 2011-09-07
Great. Learn something every day here. :D

---

### Post by latvian on 2011-09-08
I forgot to thank you for your reply and help. Thank you very much.

> **coffeecat said:**
> 

However, a 450GB Ubuntu partition is not a good use of the hard drive space you have there. Apart from the fact that Ubuntu uses a separate swap partition, if you were setting up a conventional dual-boot with Windows, it would be better to have an Ubuntu root partition of only about 20-30GB and then another large partition for storing personal data which can be accessible from both Windows and Ubuntu.
[/code]

A question, can I make the shared partition that would be accessible by Windows and Ubuntu NTFS?

---

### Post by coffeecat on 2011-09-08
> **latvian said:**
> A question, can I make the shared partition that would be accessible by Windows and Ubuntu NTFS?

That would be what I would choose.

Good luck.

---

### Post by al1x on 2011-09-08
> That's not the ideal way, you would want to add it to your fstab, a file which lists the partitions and where they are to be mounted at during startup.

There are some nice easy to use gui's for this, have a read here

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Thanks for the link! I've entered the following line to my fstab file
```
UUID=xxxxxxxxxx /media/vegapunk ntfs    rw,user,fmask=0111,dmask=0000   0   0
```
and it works fine except one thing: I cannot give the execute permission to a .exe file despite the fact that I'm running command with sudo(i.e. sudo chmod u+x file.exe, sudo chmod 777 file.exe)Any ideas? :popcorn:

---

### Post by coffeecat on 2011-09-08
> **al1x said:**
> and it works fine except one thing: I cannot give the execute permission to a .exe file despite the fact that I'm running command with sudo(i.e. sudo chmod u+x file.exe, sudo chmod 777 file.exe)Any ideas? :popcorn:

You can't use chmod (sucessfully) on a NTFS filesystem. Microsoft filesystems do not support Linux permissions. Linux permissions can only be set globally for all files when mounting the filesystem. Therefore, the only way round this would be to add the exec option in your fstab line. This will have the effect of making everything executable. When you double-click on a text file, for example, instead of opening directly in gedit the system ask you whether you want to run it or open it. This is the one major disadvantage of using a NTFS filesystem. Use it for non-executable data only. Keep executables on a Linux filesystem.

Are you sure you mean an .exe file? Or are you trying to run an Windows executable in wine?

---

### Post by al1x on 2011-09-08
> Are you sure you mean an .exe file? Or are you trying to run an Windows executable in wine?

Yes, I was trying to run a .exe file using wine.

---

### Post by latvian on 2011-09-08
What about the partition where Ubuntu is going to be installed on? What type of file system should it be? EXT3? And what about the mount point?

---

### Post by bcbc on 2011-09-08
> **al1x said:**
> Thanks for the link! I've entered the following line to my fstab file
```
UUID=xxxxxxxxxx /media/vegapunk ntfs    rw,user,fmask=0111,dmask=0000   0   0
```
and it works fine except one thing: I cannot give the execute permission to a .exe file despite the fact that I'm running command with sudo(i.e. sudo chmod u+x file.exe, sudo chmod 777 file.exe)Any ideas? :popcorn:
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by al1x on 2011-09-08
> **latvian said:**
> What about the partition where Ubuntu is going to be installed on? What type of file system should it be? EXT3? And what about the mount point?

[http://ubuntuforums.org/showthread.php?t=1133719]("http://ubuntuforums.org/showthread.php?t=1133719")
The mount point for the root will be "/".

---

### Post by al1x on 2011-09-08
> **bcbc said:**
> [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

So here it says about uid, gid and umask when I read a HowTo which says about fmask and dmask... ([https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions))
What's the difference between them?:confused:

---

### Post by bcbc on 2011-09-08
> **al1x said:**
> So here it says about uid, gid and umask when I read a HowTo which says about fmask and dmask... ([https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions))
What's the difference between them?:confused:

WorMzy seems to be the subject matter expert. Try asking in that thread ;)

---

