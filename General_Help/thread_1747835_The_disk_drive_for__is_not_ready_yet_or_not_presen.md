---
title: "The disk drive for / is not ready yet or not present"
date: 2011-05-03
forum: General Help
---

### Post by Bravo.I on 2011-05-03
I upgraded my computer from Ubuntu 10.10 to 11.04 and now the OS doesn't boot correctly. I keep getting the same error msg after selecting Ubuntu from the grub:  'The disk drive for / is not ready yet or not present.' 

Underneath that line is the other msg: 'Continue to wait; press S to skip or M for manual recovery.'

I tried them both and if i press S then it gives another err msg: 'The disk drive for /tmp is not ready or not present' ; 'Continue to wait; or press S to skip or M for manual recovery'

now if i press S then it shows a black screen with this msg:

```

mountall: Plymouth command failed
mountall: Disconnected from Plymouth

```How do i recover my system now... I don't want to reinstall the whole of ubuntu 11.04 but i just want the old system back or Ubuntu 11.04 back in working order. I f i continue to wait nothing happens except the screen goes black. I know theres a way through the command line but how?

Thanks for all your help!

---

### Post by zsung on 2011-05-03
Exact same thing is happening to me - would be great to know if there is a fix.   I can start up a maintenance terminal by pressing "M", but it's read-only, so if I want to edit /etc/fstab or anything, I'm not able to do so.

Thanks for any assistance.

---

### Post by stable on 2011-05-03
Same problem here. It is a bit frustrating because I really don't want to wipe it clean and start over again.

---

### Post by thagoat on 2011-05-03
Same damn problem. And my 2nd hard drive won't mount. I also cannot login to webmin with my user:pass. Although I can login via SSH with the same user:pass. Broken!
To boot: My Dell laptop does not work correctly with the Unity Desktop. I've never had a a single problem with Ubuntu until this upgrade, and now 2 servers and a laptop have been rendered useless.

---

### Post by Bravo.I on 2011-05-04
Hi
A lot of people seem to be having this problem and by what i'm guessing... I don't think that there's a fix at present.
Anyway I hope that a fix will show up soon... I cant wait though, I just deleted the ubuntu partition using gparted and now i'm going to reinstall 10.10 :(.
Hope theres a fix for this issue soon!

Have a great day everyone!

---

### Post by rcampi on 2011-05-09
It could be several things, but maybe the problem is due to the update didn't finished properly. If it is your case, try the following:

Press 'M' when asked to try to solve the problem manually.

In the console write the following, to remount / disk in Read&Write

mount -n -o remount,rw /

To finish the upgrade write

dpkg --configure -a

It could take several minutes.

Then reboot. 

Let me know if it works out

---

### Post by Bravo.I on 2011-05-11
Oh thanks! But i wish you'd replied sooner... I already deleted the partition so theres nothing to try now but if something like this happens again i'll sure try! Thanks again!

---

### Post by search66 on 2011-05-11
Having the same issue... Im trying rcampi's suggestion now and will let you know if it resolved the issue.

Very disappointing to say the least. I've been so happy with Lucid; I knew I shouldn't have upgraded.

---

### Post by FatAngus on 2011-05-17
Thanks rcampi 

This worked a treat for me. :KS

---

### Post by ssbarnea on 2011-05-20
> **rcampi said:**
> Press 'M' when asked to try to solve the problem manually.
mount -n -o remount,rw /
dpkg --configure -a
 - Thanks

This worked for me perfectly. Do you have an idea why this happened? I made 6 ubuntu upgrades and only one did this. Also this was on a remote location so it was really inconvenient to solve.

---

### Post by the_woodwose on 2011-05-23
Thanks rcampi, worked great.  No idea how this happened though, weird.

---

### Post by riomacho on 2011-05-26
This worked for me, thank you!  

Problem was in my case was that another user logged out during the upgrade process and the computer froze -- keyboard and mouse both.

---

### Post by flyer-fei on 2011-06-06
> **rcampi said:**
> It could be several things, but maybe the problem is due to the update didn't finished properly. If it is your case, try the following:

Press 'M' when asked to try to solve the problem manually.

In the console write the following, to remount / disk in Read&Write

mount -n -o remount,rw /

To finish the upgrade write

dpkg --configure -a

It could take several minutes.

Then reboot. 

Let me know if it works out

Very good, it totally perfect work:KS

---

### Post by bwooster47 on 2011-12-16
Well, I just cleanly installed 11.10, and I see the same message.

But - if I just wait, it manages to mount the disks and boots correctly. I am using LVM for root and other partitions.

That still seems to be a problem - why is it booting before disks are mounted? Or is there some other way to fix this?

---

### Post by innerspaceboy on 2012-02-12
I am having similar problems which began with aptdaemon and resulting in the same **/tmp is not ready** error, but none of the fixes listed above have resolved my issue.

I've posted the details [in this thread]("http://ubuntuforums.org/showthread.php?t=1924426") any and all help is greatly appreciated!

---

### Post by paapu on 2012-03-28
Thank's rcampi! Worked also for me (I seem to be a bit late with this upgrade). Terveisin, Markus:lolflag:

---

