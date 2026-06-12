---
title: "why is lost+found so  big?"
date: 2009-12-30
forum: General Help
---

### Post by kiridude on 2009-12-30
When I create new partitions in Ext4 gparted makes a very big lost+found. My (internal) partition is 406.46 GB and 6.57 GB are listed as "used." I have not put anything on this partition, and since the only file I see listed is lost+found, I am assuming that this is where the space has been allocated.

So my question is: 
1. Is this normal?
2. Can I safely reduce the lost+found size?

I will be using this partition to store movies. 

Some extra info:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6424    51600748+  83  Linux
/dev/sda2           59487       60801    10562737+   5  Extended
/dev/sda3            6425       59486   426220515   83  Linux
/dev/sda5           59487       60801    10562706   82  Linux swap / Solaris
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              49G  2.7G   44G   6% /
udev                  1.8G  332K  1.8G   1% /dev
none                  1.8G  184K  1.8G   1% /dev/shm
none                  1.8G   84K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda3             401G  199M  380G   1% /media/f473dd5f-e493-44ad-a26c-3e4a32ec9a93
```

```
H/W path               Device      Class       Description
==========================================================
/0/100/1f.2/0.0.0/1    /dev/sda1   volume      49GiB EXT4 volume
/0/100/1f.2/0.0.0/2    /dev/sda2   volume      10GiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5   volume      10GiB Linux swap / Solaris partit
/0/100/1f.2/0.0.0/3    /dev/sda3   volume      406GiB EXT4 volume

```

Thanks

---

### Post by hawthornso23 on 2009-12-30
I'm not an expert, but ...

... my understanding is that ext4 reserves a big chunk of the disk to run the journalling file system when you format the disk. I would think that this is probably where all that space is being used. It is the price you pay for the extra security under ext4. If all you are going to do is store movies on the disk and you are not going to be doing a lot of frequent writing, then maybe ext3 is good enough for you, and you don't need to devote this space to a journalling file system.  

... lost+found is for disconnected file fragments recovered during file system check. It is usually empty unless you've had some problem with your disk. I would certainly expect it to be empty on a newly formatted disk. I don't think this is where the space is being used.

---

### Post by t0p on 2009-12-30
There's a disk usage analyzer (**Applications > Accessories > Disk Usage Analyzer**) that will display how your disk space is being used in a pretty pie-chart.

Your lost+found directory should be empty after a fresh install.

---

### Post by john newbuntu on 2009-12-30
Do a "sudo du -h <fullpathtolost+found directory>" to determine its actual size.
You can even go into that directory and see what you find using the "ls -al" command.
I have a feeling it is very small.
The rest of the space used are probably allocated for superuser processor in case the drive gets full.

---

### Post by kiridude on 2009-12-30
Thanks guys for the replies.

So does that mean that if I want Ext4, I must sacrifice almost 2% of each partition?

---

### Post by QLee on 2009-12-30
[QUOTE=kiridude]Thanks guys for the replies.

So does that mean that if I want Ext4, I must sacrifice almost 2% of my partition?[/QUOTE]

If that space concerns you, you probably also want to consider your swap partition size, do you need a 10G swap?

---

### Post by kiridude on 2009-12-30
> **QLee said:**
> If that space concerns you, you probably also want to consider your swap partition size, do you need a 10G swap?

yeah, Ubuntu made it that size on installation. I'm going to shrink it down to 2GB - should be more than enough.

---

### Post by john newbuntu on 2009-12-30
Read this article on the ext3 filesystem.  ext4 is very similar:
[http://www.wiredrevolution.com/system-administration/free-ext3-reserved-blocks-with-tune2fs](http://www.wiredrevolution.com/system-administration/free-ext3-reserved-blocks-with-tune2fs)
If you need to recover more of that reserved space, you could use the command:
tune2fs -m0 /dev/sda3

---

### Post by dcstar on 2009-12-31
> **kiridude said:**
> Thanks guys for the replies.

So does that mean that if I want Ext4, I must sacrifice almost 2% of each partition?

All Journaling filesystems have an overhead, it varies depending on the type of filesystem and its features.

If you don't that care much about your data you can remove the journaling and convert it to an EXT2 filesystem.

---

### Post by kiridude on 2009-12-31
Think I've got it now. Thanx

---

### Post by rnerwein on 2009-12-31
hello
i think you ain't got it.
if you create a filesystem there is by default a reservation of 5% of the size (5% is a lot and come from small disks a long time ago) if you create a new fs you can use the option -m reserved-blocks-percentage to lower it (space is reserved for daemons running with root permisson - eg. syslogd).
to figure out the reserved szize of your already installed fs you can use: tune2fs to see all the parameters (you can change it too with this command - but don't set the size to zero !) see man pages for tune2fs and mkfs.ext4. ciao

---

### Post by kiridude on 2010-01-01
> **rnerwein said:**
> hello
i think you ain't got it.
if you create a filesystem there is by default a reservation of 5% of the size (5% is a lot and come from small disks a long time ago) if you create a new fs you can use the option -m reserved-blocks-percentage to lower it (space is reserved for daemons running with root permisson - eg. syslogd).
to figure out the reserved szize of your already installed fs you can use: tune2fs to see all the parameters (you can change it too with this command - but don't set the size to zero !) see man pages for tune2fs and mkfs.ext4. ciao

tune2fs is a pretty cool little program!

Upon some research, it seems that the reserved space is not needed if you are just storing movies or music on the partition (as I am). Is that valid? I left space on my OS partition, but set it to zero on my movies partition. 

Also, it's a bit strange that after resizing, gparted shows no change in "space used," and df shows total disk availability at 450GB when I have a 500GB disk. Did I do something wrong?

---

### Post by rnerwein on 2010-01-01
hi
i think you set your movie partition to zero - if it's full - u will recognise it :-)  . the other question was - where are my gigs gone. df shows u the usable disk-size. all other stuff like superblocks, inodetables and and and ... needs space on the disk too (and thats good that this space is not useable for normal users). just open a terminal window and execute a root shell. use fdisk to see information about your partitions ( do not play with this command !!! ).
fdisk /dev/sd3 
following the instructions (p show you details)
use q to quit
--> real programmes don't use mice <--

---

