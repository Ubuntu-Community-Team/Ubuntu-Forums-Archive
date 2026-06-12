---
title: "Crap, I think I deleted Windows =/ Help Real Quick Please"
date: 2010-10-27
forum: General Help
---

### Post by gregpxc on 2010-10-27
So I was trying to prep my HDD for a Windows and Ubuntu dual boot. Without thinking I created a partition table in GParted... did this delete all the data on my drive? Or will a windows recovery disk get it back? Please help me asap I just need short, sweet answers.

---

### Post by Vaphell on 2010-10-27
run GParted and see what hdd looks like. New partition table doesn't sound too good though.

---

### Post by gregpxc on 2010-10-27
well here's the thing...

I was having this problem in gparted

Before I even did the table thing, I would run Ubuntu from the USB and when I would look at gparted it would just say that the whole drive was unallocated but I could sill boot into windows.

Now it still says it's all unallocated but I can't boot into windows =/

---

### Post by TheSqueak on 2010-10-27
There's an app in the repositories called foremost which *might* be able to help you out here - it saved a friend of mine from having to [murder her flatmates](http://ubuntuforums.org/showthread.php?t=466087) a few years back

---

### Post by gregpxc on 2010-10-27
I don't think it's gonna happen.. I am not too good with command and nothing I just tried got anywhere.

I just wanted the pictures but I guess I will have to deal

Windows recovery wouldn't fix it though? If I put in my Windows 7 disc?

---

### Post by gradysghost on 2010-10-27
Windows recovery **might** fix it, and it **might** make it worse.  If you want, we can help you try to recover the data.  Are you able to boot to an Ubuntu desktop at this moment, either from a live CD or from your primary hard drive without further affecting the partition table?

---

### Post by gregpxc on 2010-10-27
right now I am booted into Ubuntu using a usb (im assuming with the live cd on it)

---

### Post by gradysghost on 2010-10-27
That's fine.  When you look in your Places menu, do you see anything there about your hard drive?  For example, if your drive is 120 GB in size, it might say "120 GB Filesystem", or if the partition is half of that drive, it could say "60 GB Filesystem" or something similar.  If so, you can click that to see the files on that file system.  If it's your Windows partition, FANTASTIC!  Just throw in an external drive or something and dran-n-drop your way to data recovery.

---

### Post by gradysghost on 2010-10-27
Failing that, you can launch a terminal (Applications -> Accessories -> Terminal) and give us the output of the following command:

```
ls /dev/ | grep [sh]d
```

---

### Post by gregpxc on 2010-10-27
notta... gparted and disk utility show it as unallocated space... wont let me mount it either.. unless theres a manual way to mount it that im not aware of.

---

### Post by gregpxc on 2010-10-27
> **gradysghost said:**
> Failing that, you can launch a terminal (Applications -> Accessories -> Terminal) and give us the output of the following command:

```
ls /dev/ | grep [sh]d
```

ok I got:

```
sda
sda1
sdb

```

---

### Post by gradysghost on 2010-10-27
Okay.  Try this.  I'm not sure if this is going to work for you, since the space is noted as unallocated right now, but it's at least worth trying.

Go to the terminal, run the following:

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
ls /media/sda1
```

If the second command runs without errors, you're probably alright.  The third command will list all the files on that partition.  If they're Windowsy, you can copy them off to something else using the terminal (or I think it will actually show up in Nautilus if you're able to get this far, and that may be easier on you).

---

### Post by gregpxc on 2010-10-27
> **gradysghost said:**
> Okay.  Try this.  I'm not sure if this is going to work for you, since the space is noted as unallocated right now, but it's at least worth trying.

Go to the terminal, run the following:

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
ls /media/sda1
```If the second command runs without errors, you're probably alright.  The third command will list all the files on that partition.  If they're Windowsy, you can copy them off to something else using the terminal (or I think it will actually show up in Nautilus if you're able to get this far, and that may be easier on you).

Here it is:

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /media/sda1
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
ubuntu@ubuntu:~$ ls /media/sda1
ubuntu@ubuntu:~$ 
```

I went ahead and tried the third one anyway even after the issue with the second

---

### Post by Surachinen on 2010-10-27
well, not much in the help section, but hopefully some useful advice:

1) did you have any of said pictures on web site albums? (facebook, myspace, ect?) if so you can get some of them back

2) if you can't get them back, make sure to put new ones on sites with albums (see 1) or better yet. ubuntu one!

3) well, there is no three that i can think of. but treat this as a valuable lesson in backing up your media (blank dvds are uber-cheap)

sorry for the lack of concrete help

---

### Post by gradysghost on 2010-10-27
Can you give me the output of:

```
ls /media/
```

While I look up that error?

---

### Post by gradysghost on 2010-10-27
Also try this in the meantime:

```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
```

---

### Post by gregpxc on 2010-10-27
> **gradysghost said:**
> Can you give me the output of:

```
ls /media/
```While I look up that error?


```
ubuntu@ubuntu:~$ ls /media/
sda1
ubuntu@ubuntu:~$ 

```

and

```
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
ubuntu@ubuntu:~$ 
```

---

### Post by Matt Harrison on 2010-10-27
What is the output of:
```
mount
```

This will give all of the current mountpoints.

---

### Post by gradysghost on 2010-10-27
The output of the ls /media command suggests that if the partition is mounted, it is not mounted in the /media command.  Combined with the "exclusively opened" command from mount suggests that this partition is probably not an NTFS/Windows partition, and is probably already mounted as part of the currently running OS.

Please post the output of:

```
mount
```

No arguments or anything.  Just that command by itself.

---

### Post by gregpxc on 2010-10-27
Sorry for the delay, had to switch classes

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ 
```

---

### Post by gradysghost on 2010-10-27
Okay, I don't see the device listed there.  Last ditch effort:

```
cat /etc/fstab
```

This probably won't help, though, since you're booting from a live system.

---

### Post by Matt Harrison on 2010-10-27
Yeah, fstab should just be default.

Although you can try:
```
sudo fdisk -l
```

So we can see all of your disks.

---

### Post by gregpxc on 2010-10-27
> **gradysghost said:**
> Okay, I don't see the device listed there.  Last ditch effort:

```
cat /etc/fstab
```This probably won't help, though, since you're booting from a live system.
```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$ 
```

---

### Post by gregpxc on 2010-10-27
> **Matt Harrison said:**
> Yeah, fstab should just be default.

Although you can try:
```
sudo fdisk -l
```So we can see all of your disks.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb455e505

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         975     7830528    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(973, 254, 63) logical=(974, 250, 44)
ubuntu@ubuntu:~$ 
```

---

### Post by gradysghost on 2010-10-27
Cool.  I'm betting that /dev/sda is your primary hard drive, and it's 160 GB in size.  /dev/sdb is probably the drive you're currently booting from.  An 8 GB flash drive, right?

So when we were trying to mount /dev/sda1 before, it was the right disk.  I'm not entirely familiar with fdisk, though, so maybe Matt can help out with this one.  Matt, why is there a /dev listing for a partition on this drive, but no listing for it in the fdisk output?  Could this be indicative of something useful?

---

### Post by gregpxc on 2010-10-27
those are correct and I noticed the third one also

---

### Post by Elfy on 2010-10-27
You might be able to use testdisk to recover the partition table - I've only ever used it once though so I'm not going to be helping. 

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_type_selection](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_type_selection)

There are other threads here about similar.

---

### Post by gregpxc on 2010-10-27
can't use that..  I am no good without someone telling me exactly what to type =P

---

### Post by nothingspecial on 2010-10-27
sdb1 (the third one) is the partition on /dev/sdb

If there was a partition table on /dev/sda then fdisk would list them - /dev/sda1, /dev/sda2 etc etc

You don`t have any partitions on your 160G drive.

Have a look at photorec

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Do not try to create a new partition on your drive until you have exhausted the recovery options.

And I`m not trying to be funny but -- backup the stuff you don`t want to loose.

---

### Post by Matt Harrison on 2010-10-27
The fdisk output shows that there are no partitions (same as we saw in gparted).

I'm not sure why sda1 showed in /dev/, maybe it was created before gparted killed the partitions.

I was about to recommend TestDisk as well. I'm not really sure how to use it in this case either, but it should be your best bet for data recovery at this point.

---

### Post by oldfred on 2010-10-27
It looks like partition table is missing partitions. If you have not written any data onto drive testdisk should be able to recover it.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk will show old partitions and possibly let you reinstate them.

---

### Post by for.i.am.root on 2010-10-27
> **gregpxc said:**
> can't use that..  I am no good without someone telling me exactly what to type =P

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Is a step by step tutorial to using TestDisk to recover a deleted partition.

If you were running Ubuntu full time you could use:

sudo apt-get -y install ddrescue && sudo ddrescue -vr-1 /dev/XXX recovered_data_blocks.img gddrescue.log

XXX being /dev/sda (to recover the disk) or /dev/sda1 (your *probable* Windowz partition) in your case.

This will ONLY work with journaling filesystems (works on ext3 and ext4 for sure).

Good luck.

On a side note deleting Windowz completely could be considered "practice". Just tell everybody you were testing your "mad skillz" at hacking/recovering. :)

Thanks!

---

### Post by gradysghost on 2010-10-27
Yeah, I think I'm out of options for assistance as well.  I've never used TestDisk before, but I'll start looking into it when I get some free time (almost never) and something to test with.  Best of luck, man.  Maybe you can find some documentation for TestDisk on the Interwebs somewhere?  Maybe another thread here?

---

### Post by gregpxc on 2010-10-27
Ok I got it to work! I am seeing tons of files pouring into the home directory on my flash drive. I am having some issues though. One, is there a way to restrict what is transferred (such as just pictures .png, .jpg, jpeg, bmp and so on)

I don't have enough room on my drive to bring it all over...

Also how can I delete files that tell me Im not the owner so I can't delete them?

---

### Post by Elfy on 2010-10-27
there are links in this thread - 2 of which point to a step by step

---

### Post by gregpxc on 2010-10-27
> **forestpiskie said:**
> there are links in this thread - 2 of which point to a step by step

see above post please.

---

### Post by nothingspecial on 2010-10-27
> **gregpxc said:**
> Ok I got it to work! I am seeing tons of files pouring into the home directory on my flash drive. I am having some issues though. One, is there a way to restrict what is transferred (such as just pictures .png, .jpg, jpeg, bmp and so on)

I don't have enough room on my drive to bring it all over...

Also how can I delete files that tell me Im not the owner so I can't delete them?

```
sudo rm file_you_want_to_delete
```
```

sudo rm -r folder_you_want_to_delete
```

Don`t make a mistake though.

---

### Post by gregpxc on 2010-10-27
Okay so I have NO idea what I did but my computer won't turn on or anything it's almost like bricked....


















































































No I'm just kidding. I messed around with TestDisk. Clicked some stuff (no idea what so don't ask lol)

I did a search for Intel partitions? and sure enough it found some beautiful looking windows partitions.. i think I went to all the intel partitions and clicked write? and now I am talking to you from my fully recovered windows 7 install =]

---

### Post by for.i.am.root on 2010-10-27
Congratulations!

Now comes the easy part:

Step 1. BACK UP
Step 2. Delete Windowz
Step 3. Install Linux!

:)

---

### Post by oldfred on 2010-10-27
+1 for for.i.am.root's suggestion.:)

But if you are doing dual boot. Use win7's partition tools to shrink the win7 partition, but not for anything else. Reboot win7 several times to make sure it has run chkdsk which on resize it often wants to do.

Then you can use gparted to create new partitions and use manual install or use the installer to create partitions in the free space.

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

