---
title: "Confused about ext4 file system"
date: 2010-03-08
forum: General Help
---

### Post by jz1977 on 2010-03-08
I've installed Ubuntu 9.10 and (believe) I told the installer to format all non-windows partitions. Don't recall any errors. Presumably I selected ext4.

After install and using for a while I notice in Disk Utility there is a 54GB extended partition. This contains a 46GB LVM2 partition and a 6GB ext4 partition.

The system seems to be using this tiny ext4 partition.

See df -h output:

root@bridge:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             6.4G  4.3G  1.8G  71% /
udev                  248M  292K  248M   1% /dev
none                  248M  312K  248M   1% /dev/shm
none                  248M   96K  248M   1% /var/run
none                  248M     0  248M   0% /var/lock
none                  248M     0  248M   0% /lib/init/rw
none                  6.4G  4.3G  1.8G  71% /var/lib/ureadahead/debugfs
root@bridge:~# 

Why did it not create a larger ext4 partition if it intended to use it as the main partition?

Am I expected to resize this myself with resize2fs? The man page tells me that to enlarge it, the partition must not be mounted, but it's my root partition. So do I need to boot from livecd or into some rescue mode to do this?

Thanks for any help

---

### Post by Revolutionary101 on 2010-03-08
To resize it you would need to use the Ubuntu live CD.

---

### Post by jz1977 on 2010-03-08
> **Revolutionary101 said:**
> To resize it you would need to use the Ubuntu live CD.

Okay thanks I'll try that.

Is it a bug that the installer laid out the filesystem this way?

Do I also need to shrink the LVM2 fs? Or does ext4 sit on top of this? Otherwise what is the point of this huge partition?

Are there any GUI tools available for this like qtparted?

---

### Post by audiomick on 2010-03-08
Hi. I have read about an install only making a very small partition instead of using the whole space. It is a fault, but I can't remember why it happens occasionally.
It might be useful to do
```
sudo fdisk -l
```
the last character is a lower case L and not a figure one

and post the output here. This will help people see what your total situation is and give you more accurate advice about what to do.

---

### Post by jz1977 on 2010-03-08
Thanks audiomick, here you go:

> 
root@bridge:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        2722    21832335    7  HPFS/NTFS
/dev/sda3            9281        9725     3574462+  db  CP/M / CTOS / ...
/dev/sda4            2723        9280    52677135    5  Extended
/dev/sda5            3604        3629      208813+  83  Linux
/dev/sda6            3630        9280    45391626   8e  Linux LVM
/dev/sda7            2723        3559     6723139+  83  Linux
/dev/sda8            3560        3603      353398+  82  Linux swap / Solaris

Partition table entries are not in disk order
root@bridge:~# 


---

### Post by audiomick on 2010-03-08
There is a GUI partitioning tool on the live CD.
system> administration> gparted

I don't want to give you any advice about what to do because I haven't seen the label "linux LVM" before, and don't know what it might mean.
I notice you also have a linux partition of about 200MB, I think, at sda5. Did you make that deliberately, and do you know what is on it?

---

### Post by Slim Odds on 2010-03-08
Generally speaking, the installer does what you tell it.

If you're not even sure what you selected ("presumably"), you shouldn't criticize the installer.

Next time you might want to write down what you're doing so you can refer to it later.

Also note that LVM2 allows you to move things around without repartitioning. That's what it's all about.

These should help:
[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)
[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29")

---

### Post by jz1977 on 2010-03-09
> **Slim Odds said:**
> Generally speaking, the installer does what you tell it.

If you're not even sure what you selected ("presumably"), you shouldn't criticize the installer.


I selected format all non-windows partitions. I did not use any type of advanced or manual options.
I do not recall it even allowing me to review what it had done and would have expected it to do something reasonable, not give me a tiny root partition.

I hope I would have noticed 40 Gigs of wasted space which I now have no idea how to recover.

> 
Next time you might want to write down what you're doing so you can refer to it later.

Also note that LVM2 allows you to move things around without repartitioning. That's what it's all about.

These should help:
[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)
[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

So should this ext4 partition be on an LVM for me to do this?
I've installed and run system-config-lvm
The ext4 partition in question ("Partition 7" /dev/sda7) appears under "Unitialized Entites"
If I select it and click "Initialize entity" it tells me it contains data from "/" and that all data will be lost. I guess I don't want to do this then.
Must it be an "initialized entity" before I can resize it through LVM?

When I use gparted, gparted cannot resize the ext4 partition to be any larger than it already is. I'm guessing this is because the lvm is taking up the rest of the space? But gparted does not allow me to shrink the size of the lvm, and neither does system-config-lvm, so I feel stuck here.

How should I proceed if I wish to grow my ext4 partition? If it's not managed by the lvm (do I infer this by it's "uninitialized entity" status?) can I just delete the lvm and then resize the ext4 partition?

Sorry I'm new to lvms. 
And thanks again for all of your replies.

---

### Post by jz1977 on 2010-03-09
It appears the LVM partition is from a previous older installation of fedora.

root@bridge:~# mount /dev/VolGroup00/LogVol00 /tmp/foo/
root@bridge:~# ls /tmp/foo/
bin   dev  halt  lib         media  opt   public  sbin     srv  tmp  var
boot  etc  home  lost+found  mnt    proc  root    selinux  sys  usr
root@bridge:~# 
root@bridge:~# cat /tmp/foo/etc/redhat-release 
Fedora release 8 (Werewolf)
root@bridge:~# 

So it seems the installer did not delete this :(

---

### Post by audiomick on 2010-03-09
Once again, be aware that my advice is not to be treated as definite fact. I have done a bit of partitioning, but have not encountered LVM at all, so I don't know how gparted reacts to it.
Theoretically, if you know a partition is safe to delete, you can just delete it and resize another into the space. You are right though; gparted cannot grow a partition if there is no empty space, and the space has to be adjacent to the partition you want to grow. This might make things a bit fiddly for you.

Looking at this
```

Device Boot      Start         End      Blocks   Id  System

/dev/sda4            2723        9280    52677135    5  Extended
/dev/sda5            3604        3629      208813+  83  Linux
/dev/sda6            3630        9280    45391626   8e  Linux LVM
/dev/sda7            2723        3559     6723139+  83  Linux
/dev/sda8            3560        3603      353398+  82  Linux swap / Solaris
```

we can see that the physical order of the partitions is not the numerical order, but rather
sda7, sda8 swap, sda5, sda6

You want to add the space from sda6 to sda7, but physically you have the swap partition and sda5, whatever that is, in between. I am not certain, but I think this means you will have to move your swap to get the empty space next to sda7 where you need it.

Ok, I just looked at my system to check, and it is as I thought: gparted shows the partitions in their physical order, not their numerical order. In principle, I think you will have to delete sda6 (and the adjacent sda5, if you are sure that is dead space), move your swap down to the end of the drive (and sda5 along with it, if you want to keep it), then expand sda7 into the resulting empty space.

The problem with this is that this will, as far as I know, mess up the UUID numbers of at least the swap partition, which means you will have to update Grub, and I think fstab as well.

An easier way might be to just erase sda6 (and sda5 if you want to), and create a new ext4 partition in the space to be used as a Data partition. This would at least work as a stop gap until you do your next fresh install, at which time you could "clean up" your partitioning.

---

