---
title: "Data recovery"
date: 2011-02-28
forum: General Help
---

### Post by Sir Pig on 2011-02-28
Hi,

My config is Ubuntu 10.04 installed on a drive and I use another drive to store pictures, music, etc.
While re-installing Ubuntu, I mounted my second drive as ext4 on /usr 
Since then I can't have access to my data however, I guess they are still there as I see 870Go left (the drive is 1To so the space remaining is consistent)
If I am correct, I have mounted it as ext3 and not ext4 during my previous install.

Any idea how I could recover my data?
I am afraid revert back to ext3 will format the drive and I didn't manage to find a tool to do it without format

Thanks!

---

### Post by Sir Pig on 2011-03-15
Any idea anyone?
Should I say goodbye to my beloved data?

---

### Post by indytim on 2011-03-15
I don't know how you are mounting your drive in /ext.  My first suggestion is to un-do this mounting.  My second recommendation is to create a directory (folder) in either /media or /mnt (use /media if you want to see an icon of the mounted folder on your desktop.
> 
$ sudo mkdir /media/MyData


After you have created the directory:

> 
$sudo mount /dev/sda7 /media/MyData


Using your filemanager of choice, navigate to the /media/MyData directory.  Your folders and files should now be visisble.

If you want to make the above permanent (as in happens everytime you boot, then modify your /etc/fstab file.

See 

```

$ man chown
$ man chgrp

```

For permission issues with the /media/MyData contents.

Of course put your own variables is where I have used /sda7 & /MyData

Good Luck,

IndyTim / DataMan

---

### Post by Sir Pig on 2011-03-18
Thanks for your help!

I haven't mounted the disk in /ext by ext3 and ext4 I meant the type of the disk (NTFS, ext3, ext4, etc.)
I used to mount it as ext3 but mounted as ext4 during my last install.
Do you think it has formatted the disk and all the data are lost?

---

### Post by Jagoly on 2011-03-20
Yes. Ext 4 is a different fs to Ext 3. You may be able to recover some of the data with testdisk ([http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download"))

Be careful, though. Writing new files to the partition will erase the old (deleted ones). Best to do this from a live cd.

---

