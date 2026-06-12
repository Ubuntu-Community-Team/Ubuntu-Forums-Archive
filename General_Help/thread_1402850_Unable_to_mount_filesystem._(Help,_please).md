---
title: "Unable to mount filesystem. (Help, please)"
date: 2010-02-09
forum: General Help
---

### Post by Woolio1 on 2010-02-09
It seems, every Monday and Thursday, my Dell Mini 10 with Ubuntu 9.10 (32bit) crashes. The desktop slows to a crawl, applications stop working, and the system powers off. When I try to turn it on, I get past the Circle of Friends symbol, and then I get a terminal that says,

"Mount of filesystem failed. A maintenance shell will now be started. CONTROL-D will terminate this shell and retry. -standard root terminal information here-"

When I hit CONTROL-D, I get this message.

"mountall start/starting
fsck from util-linux-ng 2.16
swapon: /dev/disk/by-uuid/57c101a9-887a-45ea(bunch more random jumble): swapon failed: Device or resource busy.
Mountall: swapon (Same string, this time with a [799] at the end.) terminated with status 255
mountall: problem activating swap. (string of numbers/letters. Still the same.)
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: Inodes that were a part of a corrupted orphan list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
mountall: fsck / [797] terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (793) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@jared-laptop:~#"

If the string is important, I'll post it here. If not, that's fine.

I'm on a Dell Mini 10 Netbook, running Ubuntu Desktop Edition 9.10, 32bit. This doesn't happen when I install software, it seems... It just does it randomly. Before it happens, my desktop lags and shuts down... But there's no Kernel Panic.

If you can help, I thank you. And if you can't help, but think you know why this keeps happening, please tell me.

-Ericson

EDIT: SOLVED: I can't thank you enough. My system's back up and running, chugging along like it normally is. And in doing this, I've learned some useful skills. Again, I can't thank you enough.

---

### Post by Richard1979 on 2010-02-09
Yes I know what this is.
Basically it's trying to mount a disk that is busy because a filesystem check (fsck) was needed.

You can bypass this by mounting the disks in a live CD and altering the /etc/fstab file (NOT the one on the live CD, it will probably be /media/sda1/etc/fstab or similar).
Change the last digit on the line which is giving you problems to a zero to skip checks on mount.

If you want more info on it, I wrote an article a few days back:
[http://www.digit4l.net/2010/02/fixing-ubuntus-device-not-ready-boot-problem/](http://www.digit4l.net/2010/02/fixing-ubuntus-device-not-ready-boot-problem/)

---

### Post by Woolio1 on 2010-02-09
Sorry if I sound stupid, but how would I go about opening it in nano? Every time I try, I get a blank nano window...

EDIT: Never mind, I found it.

---

### Post by miegiel on 2010-02-09
> **Woolio1 said:**
> Sorry if I sound stupid, but how would I go about opening it in nano? Every time I try, I get a blank nano window...

I think you need to verify the path.
```
nano /media/sda1/etc/fstab
```
also gives me an empty nano. But that's normal since the file doesn't exist for me.

Did you boot from a live-CD and mount your harddisk as **Richard1979** suggested?

---

### Post by serpentracer on 2010-02-09
I wouldn't go saying it's solved just yet.
mine has done it 2 times in 24hrs. and fsck finds all kinds of errors...stuff I didn't cause. I was just browsing the net etc and all of a sudden weird things started happening. such as menu's have no words only a bunch of 0000000.
the system crashed...you don't get a blue screen of death, instead you get....nothing. 
 
I'm currently giving up and trying something else. fedora..has way to many bugs still.  it was nothing but errors from the second it started.   kubuntu I don't like it's layout etc, when suse is done, I get to test it for a few days.
but so far none of these systems are living up to the hype.

---

### Post by miegiel on 2010-02-09
> **serpentracer said:**
> I wouldn't go saying it's solved just yet.
mine has done it 2 times in 24hrs. and fsck finds all kinds of errors...stuff I didn't cause. I was just browsing the net etc and all of a sudden weird things started happening. such as menu's have no words only a bunch of 0000000.
the system crashed...you don't get a blue screen of death, instead you get....nothing. 
 
I'm currently giving up and trying something else. fedora..has way to many bugs still.  it was nothing but errors from the second it started.   kubuntu I don't like it's layout etc, when suse is done, I get to test it for a few days.
but so far none of these systems are living up to the hype.

It just means **Woolio1** solved his problem. Besides, you should never believe a hype.

---

### Post by Woolio1 on 2010-02-10
> **serpentracer said:**
> I wouldn't go saying it's solved just yet.
mine has done it 2 times in 24hrs. and fsck finds all kinds of errors...stuff I didn't cause. I was just browsing the net etc and all of a sudden weird things started happening. such as menu's have no words only a bunch of 0000000.
the system crashed...you don't get a blue screen of death, instead you get....nothing. 
 
I'm currently giving up and trying something else. fedora..has way to many bugs still.  it was nothing but errors from the second it started.   kubuntu I don't like it's layout etc, when suse is done, I get to test it for a few days.
but so far none of these systems are living up to the hype.

Umm... I'm pretty sure none of that's happened to me. My issue is solved. Perhaps yours isn't.

---

### Post by Richard1979 on 2010-02-10
> **serpentracer said:**
> I wouldn't go saying it's solved just yet.
mine has done it 2 times in 24hrs. and fsck finds all kinds of errors...stuff I didn't cause. I was just browsing the net etc and all of a sudden weird things started happening. such as menu's have no words only a bunch of 0000000.
the system crashed...you don't get a blue screen of death, instead you get....nothing. 
 
I'm currently giving up and trying something else. fedora..has way to many bugs still.  it was nothing but errors from the second it started.   kubuntu I don't like it's layout etc, when suse is done, I get to test it for a few days.
but so far none of these systems are living up to the hype.

Using ext4?
I had serious issues under ext4, moving to the (very stable) ext3 solved several problems I had with dodgy icons.

---

### Post by chrispomeroy on 2010-02-21
> **Woolio1 said:**
> Sorry if I sound stupid, but how would I go about opening it in nano? Every time I try, I get a blank nano window...

EDIT: Never mind, I found it.

I'm dealing with the same issue and have followed the steps exactly up to this point and get a blank nano window as well.  What was the trick here?

I booted from the live CD and mounted my partition with the disk manager...

EDIT: I think I figured it out, I had to replace the full partition name in place of sda1, right?
Typing sudo nano /media/d7bff.../etc/fstab brought up the file.
Then I made the change described (deleting the last "1" in the partition and putting in "0" and exited nano and saving the modified file...

EDIT2:  It worked! thanks for this post!

---

### Post by miegiel on 2010-02-22
> **chrispomeroy said:**
> I'm dealing with the same issue and have followed the steps exactly up to this point and get a blank nano window as well.  What was the trick here?

I booted from the live CD and mounted my partition with the disk manager...

EDIT: I think I figured it out, I had to replace the full partition name in place of sda1, right?
Typing sudo nano /media/d7bff.../etc/fstab brought up the file.
Then I made the change described (deleting the last "1" in the partition and putting in "0" and exited nano and saving the modified file...

EDIT2:  It worked! thanks for this post!

Congratulations and welcome to the forum :popcorn:

---

### Post by biswajitLinux on 2010-02-22
i have tried the folowing way like first insatll naulatic package and after that edit the file rfresh_desktop but its not add in desktop context menu. plz help me?????

---

### Post by miegiel on 2010-02-22
> **biswajitLinux said:**
> i have tried the folowing way like first insatll naulatic package and after that edit the file rfresh_desktop but its not add in desktop context menu. plz help me?????

This is a completely different problem from the one discussed in this thread. Please find a thread discussing your problem and post there. Or, if you can't find a relevant thread, make a new thread here >> [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

