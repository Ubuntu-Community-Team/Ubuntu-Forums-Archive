---
title: "Need disk mirroring advice."
date: 2009-11-02
forum: General Help
---

### Post by lillooetguy on 2009-11-02
I was just given a Dell Inspiron 600 notebook. I want to leave the windows XP on it however load Ubuntu for a dual boot machine. Before I attempt a partition when loading Ubuntu, I would like to make a mirror or clone of the existing hard-drive that includes both the Windows O/S and its other unknown partition. I absolutely do not know anything of about what mirror or cloning program I should use, or how to use such a program... I looked at Clonezilla Live however I do not know if it would work on a notebook that only has Windows XP as its Operating system. Has anyone any experience with this type of backup?

---

### Post by yeleek on 2009-11-02
I use CloneZilla as a method of imaging my system partitions (though it can do whole disks).  I image off to a USB external HDD which CloneZilla supports and have had no problems with it.  Sounds like you'd want to image to a file [http://clonezilla.org/clonezilla-live/doc/](http://clonezilla.org/clonezilla-live/doc/) 

And it supports 'Filesystem supported: ext2, ext3, ext4, reiserfs, xfs, jfs of GNU/Linux, FAT, NTFS of MS Windows, and HFS+ of Mac OS. '

Just make sure you get the disks round the right way other than that - should have no issues.

---

### Post by jahst on 2010-03-01
Know this is older post.. but just in case.

I do this all the time and just use the live CD I am about to install anyway... just need to install one program.

apt-get install partimage

and then use partimage to xfer partition to external USB or whatever.

[http://www.partimage.org/Partimage-manual_Usage]("http://www.partimage.org/Partimage-manual_Usage")

I recommend using the GUI first.. but the link also gives a command line example... haven't tested it though.

---

