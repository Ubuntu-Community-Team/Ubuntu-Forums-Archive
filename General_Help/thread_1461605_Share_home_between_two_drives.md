---
title: "Share /home between two drives?"
date: 2010-04-24
forum: General Help
---

### Post by halvors on 2010-04-24
Hi!

I have an ubuntu server, and i want to set in a new disk, i need to maunt it as /home, can i mount two disks at /home an dshare files between them?

It is possible?

Halvor.

---

### Post by srs5694 on 2010-04-24
The usual way to do this is to use RAID 0 or LVM. I prefer LVM for this. Unfortunately, if you've already got a conventional /home directory with lots of files, setting this up will be a bit awkward. The basic procedure, in outline, is:


[list=1]
[*]Install the LVM tools by installing the lvm2 package.
[*]Partition the new disk and set it up to have at least one LVM partition (MBR type code 8e; or set the lvm flag in Parted; or set the GPT fdisk type code of 8e00).
[*]Use pvcreate on the LVM partition(s) you've created.
[*]Use vgcreate on the LVM partition(s) you've created.
[*]Use lvcreate to create a logical volume that will become /home.
[*]Use mkfs to create a filesystem on your new logical volume.
[*]Mount the new logical volume somewhere convenient (say, /mnt).
[*]Copy your existing /home directory to the new logical volume.
[*]If you have no separate /home partition, rename /home to /home-old and create a new (empty) /home directory.
[*]Edit /etc/fstab to mount the new logical volume at /home. (If you currently have a separate /home partition, this new entry should replace the entry for mounting your current /home partition.)
[*]Reboot and test the new configuration. Proceed with the remaining steps when you're satisfied everything is working.
[*]If you used a separate /home partition, use Parted, fdisk, or gdisk to change its type code to LVM, then use pvcreate to turn it into an LVM partition and vgextend to add it to your current volume group. You can then expand your /home logical volume using lvresize and whatever filesystem-expansion tool is appropriate for its filesystem.
[*]If you didn't originally have a separate /home partition, delete /home-old (or whatever you renamed it). If your root (/) filesystem is then ridiculously big, you can optionally use an emergency disc to shrink it, create a new LVM partition, and add it to your LVM configuration as described in the previous step.
[/list]


I realize this is a daunting set of steps if you're not already familiar with LVM configurations. Depending on the sizes of the disks, you may want to do things in some simpler way, such as:


[list]
[*]Create a regular (non-LVM) partition, move /home to it, and mount it  at /home (similar to a subset of the procedure above).
[*]Create a regular (non-LVM) partition and mount it at /home/yourdirname/somedir, where "yourdirname" is your home directory name and "somedir" is any subdirectory you care to create. You can then use the new disk at the specified location, manually deciding where to put specific files.
[*]Create an LVM partition, set up and LVM, and mount it at /home/yourdirname/somedir. This gives you the option of subsequently converting /home completely to LVM, without all the hassle of moving /home right away.
[/list]


You can Google "Linux LVM" for all sorts of LVM tutorials.

---

### Post by halvors on 2010-04-24
But to Use LVM i need too have RAID support? And i could maunt it as /home/disk1 and /home/disk2

Is it some simple way to use LVM? Some graphical tool or someting?

---

### Post by oldfred on 2010-04-24
Another way is to move some of your data from /home into the new partition as /data. It requires you to manage size a little more as you have two partitions not one combined one. My /home is now 1GB with all my data in the data partition and linked into /home so it does not look any different.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by mick222 on 2010-04-24
Do you need it to be /home or is it just a mounted partiton for data?

---

### Post by halvors on 2010-04-24
I will have alll data from my domains on the server, i think it not need to be /home, but if on eof the customer use more than 1TB i need to have /home shared by two disks/drives.

How can it be done?

halvor.

---

### Post by srs5694 on 2010-04-24
> **halvors said:**
> But to Use LVM i need too have RAID support?

No. The two have some common features, but LVM and RAID are entirely different tools.

> And i could maunt it as /home/disk1 and /home/disk2

One of the features of LVM (and RAID, for that matter) is that you can have two or more different disks or partitions that are mounted at one mount point -- so you can have ten 1TB disks that are combined into a 10TB array that's mounted at /home, and you could (with an appropriate filesystem) create a single 10TB file in that directory -- all this despite the fact that no single disk today is 10TB in size. Of course, your situation isn't that extreme, but I get the impression you want this sort of flexibility, albeit with smaller disk sizes.

> Is it some simple way to use LVM? Some graphical tool or someting?

I just checked on my Ubuntu 9.10 system, and found a couple: system-config-lvm and kvpm.  I just tried them, and they both seem to work, although I didn't do anything significant with them.

[quote=oldfred]
Another way is to move some of your data from /home into the new  partition as /data. It requires you to manage size a little more as you  have two partitions not one combined one. My /home is now 1GB with all  my data in the data partition and linked into /home so it does not look  any different.
[/quote]

Logically speaking, that's no different from mounting the new disk as /home/yourdirname/somedir and using it for storage. IMHO, mounting it in your own home directory makes more sense if you're the only user of the system, since the Unix model is to put user data in users' home directories. If the system has multiple users, setting aside another directory for data they share may make sense; or you could put one user's home directory on the second partition.

---

### Post by srs5694 on 2010-04-24
> **halvors said:**
> I will have alll data from my domains on the server, i think it not need to be /home, but if on eof the customer use more than 1TB i need to have /home shared by two disks/drives.

If you're saying that a client of yours ("client" in the business sense, not just the computer networking sense) may be creating more files than can reside on a single disk, then LVM or RAID is a practical necessity. Mounting two partitions in one directory and then sharing them in one way or another is a technical possibility; however, if you're being paid to provide business services, telling customers that they can only store a certain amount of data in particular directories makes you look unprofessional, given today's technologies. IMHO, then, you must learn enough about RAID and/or LVM to implement a configuration that enables you to present a seamless single storage area without artificial limits on the storage space available in particular directories.

---

### Post by halvors on 2010-04-24
OK, it is posible to do it with a live cd? And can i set in 1TB now and later insert a new 1TB drive? Or need i to copy it?

And need the disks/drives to be the same size or can i use 1TB and 2TB 1TB?

And it is poaible to edit the setup on /home in later time?

Halvor.

---

### Post by srs5694 on 2010-04-24
> **halvors said:**
> OK, it is posible to do it with a live cd? And can i set in 1TB now and later insert a new 1TB drive? Or need i to copy it?

And need the disks/drives to be the same size or can i use 1TB and 2TB 1TB?

And it is poaible to edit the setup on /home in later time?

Yes, you can use a live CD to set it all up. Yes, you can add disk space in the future (to either RAID or LVM configurations). The disks can definitely be different sizes for LVM. For RAID, it depends on the type of RAID you use. As to changing the setup in the future, it's certainly possible, but how difficult it will be depends on precisely what you want to do and precisely how you're setting it up.

---

### Post by halvors on 2010-04-24
OK, thanks to all, that was that i need to know ;)

---

