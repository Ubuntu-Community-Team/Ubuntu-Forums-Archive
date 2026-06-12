---
title: "Ubuntu 12.04 and MTP file systems"
date: 2012-05-19
forum: General Help
---

### Post by rybu on 2012-05-19
I recently bought an Android phone, the Samsung Galaxy.  It uses a file system that's unfamiliar to me, called MTP.    I've read up on it a little but and it ?seems? as if there's at least one bug in the 64-bit version of Ubuntu 12.04 related to MTP. 

[https://bugs.launchpad.net/ubuntu/+source/mtpfs/+bug/936165](https://bugs.launchpad.net/ubuntu/+source/mtpfs/+bug/936165)

Unfortunately for me, I do not appear to be getting quite this bug.  But I'm not sure if my problem is exactly the same.  For me, Ubuntu loads-up the file system without problems when I connect a USB cable between my laptop and the phone.  But frequently when I initiate file transfers, the transfer is cancelled with various error messages, anywhere from "unknown error" to "file already exists" (when as far as I can tell, the file does not exist) and a few other errors. 

I tried following the instructions here:

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/)

but they don't seem to be much, if any, help with this problem.

So far I've been able to transfer about 3Gb of music files to my phone.  But at present it won't let me transfer anything else over.  Sometimes if I reboot the phone and my laptop, it will let me transfer a little more.  There's still approximately 10Gb of free space on the phone so that does not appear to be the issue.

I thought I'd start this thread in case anyone having similar problems comes across a solution.

---

### Post by sorceror on 2012-05-22
> **rybu said:**
> I recently bought an Android phone, the Samsung Galaxy.  It uses a file system that's unfamiliar to me, called MTP... I tried following the instructions here:

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/)

but they don't seem to be much, if any, help with this problem.


Well, using those directions I was able to get MTP working with my Transformer Prime tablet... sort of. I can see files, and copy files to the tablet. But it's *Very Slow*.

How slow? In a test case, a 1,212 KB directory of about a dozen files transferred in 9m46.331s - or ~2KB/sec. *Floppy disks* were faster than that. Granted, they didn't hold as much. :)

No errors are being logged that I can find. It's just dog slow...

---

### Post by rybu on 2012-05-22
> **sorceror said:**
> Well, using those directions I was able to get MTP working with my Transformer Prime tablet... sort of. I can see files, and copy files to the tablet. But it's *Very Slow*.

How slow? In a test case, a 1,212 KB directory of about a dozen files transferred in 9m46.331s - or ~2KB/sec. *Floppy disks* were faster than that. Granted, they didn't hold as much. :)

No errors are being logged that I can find. It's just dog slow...

I have similar issues, except (1) sometimes the file transfers abort for no apparent reason and (2) sometimes files are transferred to the wrong directories.

---

### Post by avances123 on 2012-07-22
I have the same issues in 12.04 with mtpfs 0.9-3

---

### Post by harpinder on 2012-08-20
hey guys do you find any solution to this problem

---

### Post by rybu on 2012-08-20
> **harpinder said:**
> hey guys do you find any solution to this problem

At present I find it easiest to transfer files to my phone via wifi.   I'll send 2Gb of data to my DropBox account, then sync my phone to my Dropbox account, all via wifi.  

You'd think a direct connection would be simpler!  

I haven't been able to get my phone to talk to my laptop via bluetooth or a local wifi network.

---

### Post by wxnker on 2012-08-23
I'm on 12.10 and I've installed Gmtp, that is mentioned in the comments in the OMG Ubuntu guide. I haven't used it much, but it seems to at least kinda work. It took it quite a while to connect to the phone (Samsung Galaxy Nexus). At first I didn't think it would connect, but then it came through. 

So far I did:

1. transfer files to PC
2. transfer mp3's to Phone (each mp3 gave me an error (that I had to approve), but the transfer seemed to work).
3. Delete files on the phone.
4. Create folders on the phone.

That's pretty much it so far. 

All in all Gmtp feels a little buggy, but the interface is nice, it wasn't that slow and it did perform the tasks I tried. So I guess you guys could it give it a try.

Or...you could use ADB. :-)

---

### Post by cristianpark on 2012-09-14
My solution so far is the use of SSHDroid on the S3 and FileZilla on the Linux Box but I want to mount the filesystem instead, I haven't found anything reliable, libmtp doesn't connect and the Ubuntu 12.04 default drops connection

---

### Post by cristianpark on 2012-09-26
Sorry for the double post but I want to give new information. I tested this on Arch Linux (on Ubuntu couldn't install it) [1] and works good (but I faced some problems when iddle) and found this [2] that works with ADB as backend and it's more reliable in my experience. I hope this help you in your quest.

My tests were with a Samsung Galaxy S3

[1] [https://github.com/hanwen/go-mtpfs](https://github.com/hanwen/go-mtpfs)
[2] [https://github.com/sole/aafm](https://github.com/sole/aafm)

---

### Post by Jay Aristide on 2012-10-11
> **cristianpark said:**
> Sorry for the double post but I want to give new information. I tested this on Arch Linux (on Ubuntu couldn't install it) [1] and works good (but I faced some problems when iddle) and found this [2] that works with ADB as backend and it's more reliable in my experience. I hope this help you in your quest.

My tests were with a Samsung Galaxy S3

[1] [https://github.com/hanwen/go-mtpfs](https://github.com/hanwen/go-mtpfs)
**[2] [https://github.com/sole/aafm](https://github.com/sole/aafm)**

First time poster on these forums. Basically, I made this account just to thank you :) It amazes me that something like mtp support isn't built into ubuntu, but the second option, here, aafm, is working wonderfully :)

Thanks

---

### Post by linfidel on 2013-02-10
I know this thread is a bit old, but I've been struggling with this with my Samsung Galaxy Tab 2.  Interestingly enough, Calibre, the ebook organizer, has no problem recognizing the tablet with no additional drivers and no manual mounting.  I connect the tablet, and Calibre recognizes it, and can send file to both internal and external memory.

I had 32-bit 12.04 installed, and go-mtpfs worked well, but I finally switched to 64-bit, and it doesn't work that well.  It works, but seems to have problems, especially with Nautilus.  I set it up manually, since I don't use the unity ui, so it's possible I did something different with installing software, since the previous system had things installed haphazardly along the way to finding go-mtpfs, and I wasn't sure exactly what was necessary, or even what was installed for sure.

If anyone has more information, perhaps you could post it here.  Otherwise, maybe my experience will be helpful to someone.

---

### Post by dspisak on 2013-05-27
Hi, all.
I could not get 10.04 to recognize my Fujitsu Stylistic M532 on MTP no matter what I tried.  It would recognize only PTP.  I upgraded to 12.04 and tried mtpf, mtp-tools, Qlix, Calibre, and on and on.  The only program that works is gmtp.  It is a little slow to recognize and connect to the M532, but once connected transfer rates are pretty good (an 11 MB jpg in about 5 seconds).

---

### Post by efflandt on 2013-05-27
I have never been able to get MTP to work in 12.04 for my Galaxy S3. And after recently reinstalling my system due to a failing hard drive I tried go-mtpfs and same errors that it cannot connect, tries to reset, but that fails.

With or without mtpfs the file manager (nautilus?) only shows the root directory of internal storage and SD.  If I switch the phone to PTP I can see internal storage, but not the microSD. WinXP or Win7 have no trouble connecting and transferring files.

So I have been using **AndFTP** Android app to sftp to/from Linux from the phone (using my Linux ssh key). I also have **ConnectBot** and **SSH Server** apps, so I can ssh from the phone or sftp to it from Ubuntu (also using Linux ssh key).

---

