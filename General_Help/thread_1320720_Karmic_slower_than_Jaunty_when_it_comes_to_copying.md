---
title: "Karmic slower than Jaunty when it comes to copying files"
date: 2009-11-09
forum: General Help
---

### Post by gully on 2009-11-09
Hi, 
I've recently upgraded from Jaunty to Karmic, just the upgrade without a clean install.
I have two partitions with reiserfs filesystems (one is my "storage", the other one is where Ubuntu is installed) and a third partition with Windows 7 on it (NTFS of course.)

The thing is that under Jaunty I could copy files from Ubuntu to Windows at about 35mb/s, copying between the two reiserfs partitions got me similar speeds.
Now with Karmic I only get about 8mb/s (even when copying between reiserfs partitions), I don't get it, Karmic is supposed to be equal or faster at everything, right?

Did anyone else encounter this problem and fix it?

---

### Post by Giblet5 on 2009-11-09
I have issues with this post.

Who told you Karmic is faster at everything? Does this person only offer advice like that to you after a fourth pint?

Nobody told me that. I've noticed that ext4 is pretty zippy at some things, and  I wouldn't use reiserfs unless a customer spec'ed it explicitly.

If you don't know how to tune filesystems, why are you bothering to benchmark their performance? Attempts at the latter imply knowledge of the former...

---

### Post by gully on 2009-11-09
No one told me it would be faster, I just assumed it wouldn't be slower.

I can't use EXT4 because that would require a clean install and I don't wanna go there: it's a lot of work (to re-tune every setting like it was, and getting everything to work properly.)
It shouldn't be necessary either since Jaunty didn't have this problem.

Lastly, it's not a benchmark, I copy large amounts huge-files back and forth between Ubuntu and Windows on a regular basis so the difference between 35mb/s and 8mb/s often means hours of waiting, that's why it's bugging me.

---

### Post by Giblet5 on 2009-11-09
Oh.

It's possible that some default mount option changed from jaunty v Karmic... I'd cast a wary eye at the defaults for atime and relatime on NTFS and reiserfs.

Check how you're mounting that NTFS filesystem. Is it doing something dodgy like mounting it with nls=iso8859-1?

You might also want to verify that NTFS is mounting with udma support (hdparm -d).

I'm showing 81MB/s ext3 to NTFS on single large (4G) files. It goes to 88MB/s going the other way. Mounted with explicit noatime,norelatime options. A bit more than 10x the performance you're seeing.

---

### Post by gully on 2009-11-09
Thanks, and now that you mention it, Karmic does indeed have a new mountmanager and it shows my NTFS partition mounted like this: atime,suid,mand,nouser,auto,rw,dev,exec,async,umask=777,fmask=777,dmask=666,default,no_detach so no "noatime", I assume the 777 and 666 numbers are permissions and that they are fine, there is also an option that says "all input from/output from to the filesystem should be done synchronously (it's unticked, when I tick it the ...exec,ASYNC,umask... part becomes ...exec,SYNC,umask...), should I tick this and change atime to noatime?

---

### Post by Giblet5 on 2009-11-09
> **gully said:**
> Thanks, and now that you mention it, Karmic does indeed have a new mountmanager and it shows my NTFS partition mounted like this: atime,suid,mand,nouser,auto,rw,dev,exec,async,umask=777,fmask=777,dmask=666,default,no_detach so no "noatime", I assume the 777 and 666 numbers are permissions and that they are fine, there is also an option that says "all input from/output from to the filesystem should be done synchronously (it's unticked, when I tick it the ...exec,ASYNC,umask... part becomes ...exec,SYNC,umask...), should I tick this and change atime to noatime?

I'd play with it. I'd expect sync to be slower but that's not necessarily so.

The atime option will slow things down a bit, and should be disabled unless you need audit trail capability.

The mand option could slow things down, but I'd expect it to only affect transfers of many small files. If you'll only access files on the disk from one account, I'd use nomand.

Make sure you're using DMA via hdparm, too.

---

### Post by gully on 2009-11-09
I tried using hdparm using this guide: [http://articles.techrepublic.com.com/5100-10878_11-5031573.html](http://articles.techrepublic.com.com/5100-10878_11-5031573.html) but some of those thing didn't work with my drive, I read somewhere else that hdparm doesn't play nice with SATA drives, so I installed "sdparm", but I think it uses different commands...

"/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device"

and 

"/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support    =  0 (default)"

Are the errors I get when using hdparm.

Edit: I get 70mb/s in Windows 7 (copying files within the NTFS partition), the slow speeds in Ubuntu seem only apparent with larger files as I could copy 180mb file within 2-3 seconds, even 1.1gb files will copy with 25mb/s, while a 2.2gb file takes 5 minutes with 8mb/s, Windows doesn't make this distinction.

My harddrive is a Seagate ST31000528AS (1tb, 32mb cache, 7200rpm, SATA), Ubuntu is 32bit, Windows is 64bit, I have 6gb of memory.

---

