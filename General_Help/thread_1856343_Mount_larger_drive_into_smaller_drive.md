---
title: "Mount larger drive into smaller drive"
date: 2011-10-08
forum: General Help
---

### Post by amainejr on 2011-10-08
I've got 2 drives, the root bootable drive is 500GB partitioned with 1GB of swap space and only using around 40GB of disk space running Ubuntu 11.04 Desktop.  I've got a mountable 1TB hard drive that now contains around 450GB of stuff on it.  When I mount that drive under /media/Storage, I get a warning about disk space going to run out soon.  Shouldn't I have another 500+ GB of available storage?  It seems to me like the mounted drive is taking up "virtual" space.  Is there a way I can mount this in parallel to the root drive or access the files on it without mounting it perhaps?

---

### Post by Elfy on 2011-10-08
How do you mount it ?

I've got a 1Tb drive mounting at boot into my other _much_ smaller drive.

I have mine in fstab.

UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/music ext4 defaults 0 2

---

### Post by amainejr on 2011-10-08
```
/dev/sdc1       /media/Storage  ntfs-3g defaults,user   0       0
```

That is what's in my fstab.  I got to looking at my fdisk table for /dev/sdb, and I must have been up on a weekend trip when I installed the desktop OS.  For some reason my partitions look like this:

```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6225    49998848   83  Linux
/dev/sdb2            6225       60802   438384641    5  Extended
/dev/sdb5            6225       60802   438384640   82  Linux swap / Solaris
```

I wrote out 50 gigs of disk space and 450 gigs of swap space.  A little bass ackwards there.  I'm wondering if it's possible to resize that /sdb1 partition to 450 without losing my file structure.  I don't have anything on there really, so it wouldn't be a big deal to reinstall.  Even at that, I don't see why I have 45% of my drive space free until I mount that other drive.

---

### Post by Elfy on 2011-10-08
Can you mount the drive and then run this - paste the result

```
mount && df -h
```

---

### Post by amainejr on 2011-10-08
```
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/albert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=albert)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)
/dev/sdc1 on /media/Storage type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              47G   45G   33M 100% /
none                  1.9G  712K  1.9G   1% /dev
none                  2.0G  4.7M  2.0G   1% /dev/shm
none                  2.0G  436K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sdc1             932G  297G  635G  32% /media/Storage
```

Exactly what I thought.  How can I resize /dev/sdb1 to use more space from /dev/sdb5 without tearing up the filesystem?

---

### Post by Elfy on 2011-10-08
I'd be interested to see the mount with the external unmounted.

But as far as resizing goes, boot the livecd/usb - choose try ubuntu.

Start gparted - partition editor.

Right click on swap partition - swapoff

Then you need to resize the swap to a more suitable size, then resize the extended - then you will have space outside the extended which you can use to increase sdb1. 

To be honest though I'd be more inclined to delete swap and the extended, resize the sdb1 and create a new swap. 

Once you've done that - mount the drive 

```
sudo mkdir /mnt/tmp
sudo mount -t ext4 /dev/sdb1 /mnt/tmp
```

In the terminal run ```
sudo blkid
```

Note the UUID's

Now open the fstab file

```
gksudo gedit /etc/fstab
```

Make sure that the UUID's match the ones previously noted

Change any of necessary, you might need to reinstall grub

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

---

### Post by amainejr on 2011-10-08
Not saying your solution is wrong here by any means, because I really don't know a whole lot about the inner workings of hardware in linux, but what's the theory behind that?  Do you have a reference that explains that or is this from personal experience?  I do a lot of web server administration at work in apache, but I've played with linux for years now, doing all sorts of stuff.  I'm still only an intermediate user though and would like to know more.  I plan on taking some electronics development courses a little later, after I get my degree, so I think knowing a little more about hard disk structures and how linux handles them would come in handy as a head start.  Could you point me in the right direction?

---

### Post by amainejr on 2011-10-08
```
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/albert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=albert)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              47G   45G     0 100% /
none                  1.9G  712K  1.9G   1% /dev
none                  2.0G  700K  2.0G   1% /dev/shm
none                  2.0G  436K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock

```

There is the mount && df -h command after I issued a umount /media/Storage command.  I'm fairly sure now that the mount isn't the issue, but my negligence.  Luckily, that install was done recently, and I have everything stored on the storage drive, just for this type of incident.  

Thanks for all your help.

---

### Post by Elfy on 2011-10-08
> Do you have a reference that explains that or is this from personal experience? What are you referring to?

Fstab - plenty of references to that on the net - there's one on the buntu wiki - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you're talking about UUID changes - I'd expect there to be lots of references to that as well - but personally it caught me once. 

If you mean 

> To be honest though I'd be more inclined to delete swap and the extended, resize the sdb1 and create a new swap. that would be personal experience - I can't see the point in doing anymore work than necessary and resizing swap rather than editing fstab would take longer.

Thanks for rerunning mount - I'd suspect that the majority of the 45Gb is in your /home.

If 
> Luckily, that install was done recently, and I have everything stored on the storage drive, just for this type of incident. implies you intend to reinstall without worrying about data then I would delete all the partitions, recreate to the size you require - run the installer - choose Something Else and manually specify the / (and seperate /home if you choose to do so) mountpoints in the Edit Partition window. Swap will take care of itself assuming it's created prior to running the installer .

---

### Post by amainejr on 2011-10-08
I was talking about references that explain the actual process of what happens when you resize partitions and move stuff around.  More along the lines of the inner workings of fstab and the mount command.  I can probably just go through the package source code to get an idea about that.

I had used this box as a test for virtual machines using VMWare 2.0.2.  So, yes, you were right about that.  I think I will just delete everything and start from scratch.  Thanks for everything.

---

### Post by Elfy on 2011-10-08
> I was talking about references that explain the actual process of what happens when you resize partitions and move stuff around. I have absolutely no idea at all - I just use it :)
> 
More along the lines of the inner workings of fstab and the mount command.Fstab's the file that tells the system what to mount and where when it boots.

The man pages will tell you in more detail.

man fstab
man mount

> Thanks for everything.Welcome.

---

