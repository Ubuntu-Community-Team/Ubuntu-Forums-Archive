---
title: "checking free hard disk space"
date: 2012-02-20
forum: General Help
---

### Post by Taigen on 2012-02-20
I am a little confused as to where my memory is. I installed ubuntu 11.10 with wubi and wasnt sure how big the partition I picked was. So I used the wubi guide [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371) to resize my partition using the file and made my ubuntu partition 20gb. The problem im having is I still cant download anything because ubuntu says I dont have enough space. I was kind of wondering what I might have done wrong or if you guys have any ideas to get me started.

I took some pictures of my system monitor. It says 17.5 gb free but it shows its full on /dev/loop0

---

### Post by Taigen on 2012-02-20
Error Message:

There is not enough room on the disk to save /home/taigen/Downloads/et-linux-2.60.x86.run.part.

Remove unnecessary files from the disk and try again, or try saving in a different location.

Download Link:

[http://shacknews.s3.amazonaws.com/fileshack/action/wolf_et/et-linux-2.60.x86.run?AWSAccessKeyId=AKIAJQD4TTOOWFQNWMGA&Signature=SBQOO%2B05BGu0%2Bqz5izB4NaH8dcM%3D&Expires=1329783539](http://shacknews.s3.amazonaws.com/fileshack/action/wolf_et/et-linux-2.60.x86.run?AWSAccessKeyId=AKIAJQD4TTOOWFQNWMGA&Signature=SBQOO%2B05BGu0%2Bqz5izB4NaH8dcM%3D&Expires=1329783539)

---

### Post by 3rdalbum on 2012-02-20
Wubi does not do partitioning, it installs Ubuntu into a file.

Unfortunately it looks like you've told it to make a 6.3 GiB (difficult to read on my screen, it might be 4.3) file, which is not exactly spacious for Ubuntu.

You do have 17 GiB free space, but that's within the real partition and/or any additional partitions on your computer, not within the Ubuntu file. If you're desperate you could start storing data on those separate partitions.

I believe there are HOWTOs to help you increase the size of the Ubuntu file, or you could back up your data and do a real dual-boot installation of Ubuntu, taking care to specify a sufficient partition size in the installer. 10 GiB is enough for all the programs you're likely to install, but allow more for your user files if possible.

---

### Post by oldos2er on 2012-02-20
I changed your thread title since RAM (memory) and hard disk space are two different things.

---

### Post by efflandt on 2012-02-20
It looks like your Linux filesystem (actually a loop mounted file in your case) is 6.3 GB and you only have about 44 MB free.

Generally 8 GB is recommended as a minimum, like if running Ubuntu from a USB memory stick.

If you have about 17 GB free in your Windows partition, that is not enough room to have used the automated method in your link to have made Ubuntu 20 GB, so maybe the attempt to enlarge it failed.  Or if you did have enough room then, maybe you did not properly rename the files from MS Windows to use the new bigger file as root.disk.

From Windows see if there is another, but larger file in the same directory as your root.disk.

---

### Post by bcbc on 2012-02-21
> **Taigen said:**
> I am a little confused as to where my memory is. I installed ubuntu 11.10 with wubi and wasnt sure how big the partition I picked was. So I used the wubi guide [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371) to resize my partition using the file and made my ubuntu partition 20gb. The problem im having is I still cant download anything because ubuntu says I dont have enough space. I was kind of wondering what I might have done wrong or if you guys have any ideas to get me started.

I took some pictures of my system monitor. It says 17.5 gb free but it shows its full on /dev/loop0

That resize script duplicates the virtual disk (root.disk) to a new one (new.disk). You can check whether it's there in the /host/ubuntu/disks folder.
You have to reboot into Windows and switch them over before you get the benefit of the larger size. (Rename root.disk to oldroot.disk and new.disk to root.disk).

So, I assume that's what happened if you ran the resize and it didn't give you any errors.

---

