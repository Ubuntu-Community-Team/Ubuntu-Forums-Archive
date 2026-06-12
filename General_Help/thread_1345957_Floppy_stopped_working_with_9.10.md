---
title: "Floppy stopped working with 9.10"
date: 2009-12-04
forum: General Help
---

### Post by AKADAP on 2009-12-04
At least I think it happened with 9.10.

I had used the floppy successfully when 9.04 was installed, but when I tried recently, the system would not detect any media in the drive. I tried several floppies, and two computers. One computer is a 32 bit machine the other is 64. both running 9.10. A third machine running FreeNAS was able to read and write one of the floppies tested in the other two machines. Both machines had working floppy drives previously, and no hardware changes were done in the mean time.

If I bring up the Disk Utility, and click the Detect Media button, the disk spins, activity light comes on, but it reports "No Media Detected".

---

### Post by AKADAP on 2009-12-06
Bump.

Is anyone else's floppy drive working? Is this common, or am I the only one with this problem?

---

### Post by lechuky on 2009-12-07
I have the same problem but with 9.04

Have already change /ect/fstab and /etc/modules, also modprobe floppy.

But can't mount the drive even manually.

---

### Post by dathem on 2009-12-07
> **AKADAP said:**
> Bump.

Is anyone else's floppy drive working? Is this common, or am I the only one with this problem?


Hello, I have the same problem with 9.10 not seeing any media in the floppy drives, on multiple computers. I have a friend with the same issues.

---

### Post by TheOnlyMrK on 2009-12-08
I'm having this problem too. Had no idea it wasn't working until yesterday when I found a pile of old floppy disks and thought it'd be fun to see what stuff was on them. They're perfectly good floppy disks, the floppy drive I'm unsure because I pulled it out of an old computer, but it had no problems working when I used Windows 7 so I'm pretty sure it's Ubuntu's fault.

---

### Post by TheOnlyMrK on 2009-12-21
Update: I installed Xubuntu on another one of my desktops (it's specs on the last line of my signature) and the floppy drive works fine. So I'm wondering if this is an Ubuntu only problem. Has anyone else experienced this/does your floppy drive work in Xubuntu?

---

### Post by ron999 on 2009-12-21
@TheOnlyMrk + dathem
This has been discussed in a thread here:-
[http://ubuntuforums.org/showthread.php?t=1352401]("http://ubuntuforums.org/showthread.php?t=1352401")

---

### Post by TheOnlyMrK on 2009-12-21
> **ron999 said:**
> @TheOnlyMrk + dathem
This has been discussed in a thread here:-
[http://ubuntuforums.org/showthread.php?t=1352401](http://ubuntuforums.org/showthread.php?t=1352401)

Thanks.

---

