---
title: "How to increase an ext4 partition size without data loss"
date: 2012-03-26
forum: General Help
---

### Post by johnsr11 on 2012-03-26
I am running Ubuntu 11.10 headless and I am currently trying to increase my partition size on my 2nd hard drive without loosing any data, I was wondering if anyone could help me with this.  Greatly appreciated.

---

### Post by elliotn on 2012-03-26
use Gparted

---

### Post by johnsr11 on 2012-03-26
I have no GUI to use gparted, also, I do not have a cd to boot from, or a cd drive, since I have removed them from my server.

---

### Post by gsgleason on 2012-03-26
You cannot do this from the mounted filesystem, so you will have to boot to something else.  How about a USB thumb drive with a live image?

---

### Post by johnsr11 on 2012-03-26
This is on a 2nd hard drive.  I can't just unmount the drive and partition it?  It is not my primary hard drive

---

### Post by Mark Phelps on 2012-03-26
Found the link below, it's for ext3 -- don't know if it will work on ext4: 

[http://serverlinux.blogspot.com/2008/01/resizing-partition-in-linux-with-parted.html]("http://serverlinux.blogspot.com/2008/01/resizing-partition-in-linux-with-parted.html")

---

### Post by gsgleason on 2012-03-26
> **Mark Phelps said:**
> Found the link below, it's for ext3 -- don't know if it will work on ext4: 

[http://serverlinux.blogspot.com/2008/01/resizing-partition-in-linux-with-parted.html]("http://serverlinux.blogspot.com/2008/01/resizing-partition-in-linux-with-parted.html")


According to RedHat it will work.
[http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ext4grow.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ext4grow.html)

You will have to make sure the containing block device (like a partition or a logical volume, etc) is resized first.  This generally involves deleting the partition and re-creating it with the same starting block.

This is scary, yes, and this is why many people use gparted.

It might be a good idea to practice on another expendible partition first.

Also, gparted is just the graphical version of parted, which will do this as well.

[http://en.positon.org/post/Resize-an-ext3-ext4-partition](http://en.positon.org/post/Resize-an-ext3-ext4-partition)

You can also have an X server running on your laptop or whatever, and use X11 forwarding to view the X client from your laptop.  This is a nice way to use graphical apps on a server from a remote connection.

---

### Post by Photonic Nature on 2012-09-09
> **gsgleason said:**
> You cannot do this from the mounted filesystem, so you will have to boot to something else.  How about a USB thumb drive with a live image?

**As of ext3 and kernel 2.6, you can change the size of a live file system, But Not a Live Partition... gsgleason is correct! **
So in a case like this one where no optical drive is available, temporarily reactivate your USB / Boot support and live boot from a stick using gparted.* 
*(see notes below regarding outdated (CLI) parted info that you may encounter, however, those notes do not apply to the latest stable GParted as it works just fine with ext3 & 4.)
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")
How-To, Bootable flash drives:
[http://nims11.wordpress.com/2011/09/04/tutorial-bootable-flash-drives/]("http://nims11.wordpress.com/2011/09/04/tutorial-bootable-flash-drives/")

[http://linux.die.net/man/8/resize2fs]("http://linux.die.net/man/8/resize2fs")
> The resize2fs program does not manipulate the size of partitions. If you wish to enlarge a filesystem, you must make sure you can expand the size of the underlying partition first.
...
The resize2fs program will resize ext2, ext3, or ext4 file systems. It can be used to enlarge or shrink an unmounted file system located on device. *_If the filesystem is mounted, it can be used to expand the size of the mounted filesystem, assuming the kernel supports on-line resizing. (As of this writing, the Linux 2.6 kernel supports on-line resize for filesystems mounted using ext3 only.)_*.

The parted(8) man page in every release of ubuntu is outdated from 2007, even in 12.04 LTS which installs by default parted version 2.3 which is a stable release from back in May 2010, where as of this writing the current stable release is 3.1.(March 2012) 
~Why the man pages and packaged version have not been updated in the repositories, I don't know.~ ??? 

Previously posted link references by others above erroneously refer to using resize2fs as the alternative to using parted due to old bugs in parted where ext3 support was still alpha as every outdated man page will tell you to this day in the KNOWN ISSUES section as follows: 
[http://linux.die.net/man/8/parted]("http://linux.die.net/man/8/parted")
> **parted(8) - Linux man page (2007)**
KNOWN ISSUES
ext3 filesystem functionality does not currently work. To manage ext3 type filesystems use tools like resize2fs(8) or mke2fs(8). Note that the currently supported ext2 filesystem will be deprecated once ext3 support is finalized. Further note that ext3 support will have limited functionality that is yet to be defined. Use tools like resize2fs(8) and mke2fs(8) to manage these types of filesystems.
To manually resize an ext3 filesystem and/or a partition use resize2fs(8), fdisk(8) or similar tools. For LVM situations, you will need to use the LVM commands to resize the LVM elements.

**Now Remember!** "The resize2fs program does not manipulate the size of partitions."

I do know that parted/GParted are dropping filesystem mucking support and will only concentrate on Partitions, therefore; filesystem expansion after partition expansion will / may still have to be handled by other tools as outlined above.

The Live GParted image is now a mini-Debian distro of sorts that offers additional tools such as Screenshot, Terminal (minimal bash), Network config, & a Web Browser for your convenience.

The 'parted' project is looking for help, so if you are an able brained passerby... please see if you can give em a hand. 
[http://savannah.gnu.org/people/?group=parted]("http://savannah.gnu.org/people/?group=parted")

**_Reference links:_**
_GParted_
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

_parted_
[http://www.gnu.org/software/parted/]("http://www.gnu.org/software/parted/")
[http://www.gnu.org/software/parted/manual/]("http://www.gnu.org/software/parted/manual/")
[http://savannah.gnu.org/projects/parted/]("http://savannah.gnu.org/projects/parted/")

How-To, Bootable flash drives:
[http://nims11.wordpress.com/2011/09/04/tutorial-bootable-flash-drives/]("http://nims11.wordpress.com/2011/09/04/tutorial-bootable-flash-drives/")

---

