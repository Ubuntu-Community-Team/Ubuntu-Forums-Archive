---
title: "/home/ problems..."
date: 2010-05-30
forum: General Help
---

### Post by SavageWolf on 2010-05-30
Uh, I was following this: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/) to move home to it's own partition. Something went wrong and now home appears to be empty...

The computer now doesn't boot (It bombards me with a list of error messages), I am posting this from the installation disk of Ubuntu 9.something (Try without installing).

Generally, I was trying to fix it, making it worse, here is the current situation:

* /media/disk/home is empty.
* /media/home is also empty.
* /media/disk/old_home contains what I hope to be a correct home folder.
* ubuntu@ubuntu:/media/disk/old_home$ find . -depth -print0 | cpio --null --sparse -pvd /media/home brings up the following errors for each file:
cpio: /media/home/./(Path to the file): Cannot stat: No such file or directory
cpio: cannot make directory `/media/home/./(username)': Permission denied

---Disks---
/dev/sda1/ - /media/disk/ Root drive, /.
/dev/sda3/ - /media/home/ home is on this drive when it boots... I THINK...
/dev/sda4/ - /media/homes/ Empty drive

---

### Post by WorMzy on 2010-05-30
I presume you want your home folder to be stored at the partition mounted at /media/home?

Copy the contents of /media/disk/old_home to /media/home/ with
```
cp -pr /media/disk/old_home/* /media/home
```

Then edit /etc/fstab so that Ubuntu will mount your home partition in the right place at boot by adding the following:
```
/dev/sda3 /home ext3 defaults 0 0
```

change the ext3 to whichever ext you've formatted the partition as.

---

### Post by Ozymandias_117 on 2010-05-30
> **SavageWolf said:**
> Generally, I was trying to fix it, making it worse, here is the current situation:

* /media/disk/home is empty.
* /media/home is also empty.
* /media/disk/old_home contains what I hope to be a correct home folder.
* ubuntu@ubuntu:/media/disk/old_home$ find . -depth -print0 | cpio --null --sparse -pvd /media/home brings up the following errors for each file:
cpio: /media/home/./(Path to the file): Cannot stat: No such file or directory
cpio: cannot make directory `/media/home/./(username)': Permission denied

---Disks---
/dev/sda1/ - /media/disk/ Root drive, /.
/dev/sda3/ - /media/home/ home is on this drive when it boots... I THINK...
/dev/sda4/ - /media/homes/ Empty drive

I can't tell by something you're saying, Did you successfully copy your home directory to another partition? Or did that fail?

---

### Post by Ichido on 2010-05-30
Boot you PC from the Ubuntu Disk.
In the Terminal, run....  "gksu nautilus" which will run Nautilus as "root" so you can change Permissions, move, copy files from the /dev/sda3/ "/home" into your new /dev/sda4/ ? "/home".

---

### Post by SavageWolf on 2010-05-30
WorMzy's solution worked! I assumed it wouldn't because, as the guide put it: "Since the “/home” directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide:"

---

### Post by WorMzy on 2010-05-30
I can't say for sure whether any hard/soft links don't work any more, but I've never noticed any problems since I put my home onto a separate partition. :)

---

