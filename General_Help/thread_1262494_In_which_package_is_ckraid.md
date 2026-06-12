---
title: "In which package is ckraid?"
date: 2009-09-09
forum: General Help
---

### Post by jamesmh on 2009-09-09
Greetings all:

I have a raid 1 array (only 2 disks) on my Ubuntu Januty machine.  I had a power failure and I seem to have a problem with my raid array (on login I get a long list of ata2.01 errors, see below*).  The simple solution would be to just run /sbin/ckraid... except... where the hell is it?

The no brainer would be that it would be provided by the package "raidutils", or maybe even "mdadm" but neither of them provide ckraid.  Can someone tell me in which package I find this basic utility, or at least what is the ubuntu-esqe way of checking my raid array?

Thank in advance.

~James

* excerpt from dmesg:
<snip>
[19541.977036] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0 frozen
[19541.977046] ata2.01: cmd a0/01:00:00:30:09/00:00:00:00:00/b0 tag 0 dma 2352 in
[19541.977048]          cdb be 04 00 00 98 18 00 00  01 78 00 00 00 00 00 00
[19541.977049]          res 40/00:02:00:0c:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[19541.977053] ata2.01: status: { DRDY }
</snip>

---

### Post by tgrimley on 2009-09-10
You didn't say what the raid type was, so I'll assume you have a mdadm array.. in which case you can check on things by 
```
cat /proc/mdstat
```

ckraid has gone away I think. you can also just check the file system on top of the array?

---

### Post by jamesmh on 2009-09-10
Ah sorry.   It's a mdadm software raid 1.  By "check", I meant the raid equivalent of fsck.  TLDP's Software RAID HOWTO says not to run fsck directly on the file system on top of the array, but that document hasn't been updated in 10 years.  So if you're telling me that I now can just fsck it, then that's very helpful.

---

### Post by tgrimley on 2009-09-10
It would make sense if it said not to fsck the individual disks, but I don't know of a reason not to fsck the array file system.  I would look into it more before you do anything.

mdadm will once a month resync the array to verify everything is okay, and in the meantime /proc/mdstat will indicate an error

---

### Post by jamesmh on 2009-09-10
I just forced a fsck on reboot (on /dev/md0) and after that everything booted fine.  I'll mark this as resolved; thanks for the help.

As an aside, I'll note that ubuntu's boot was really, really slow / unresponsive after the first power failure, when the array was resyncronizing for about an hour or so, which led to me not understanding what was going on.  Basically it went like this:

1) Power failure during disk operations... I have to reboot
2) Machine boots and gdm starts... everything seems to be OK, I get the login screen
3) I login
4) gnome begins, but I get the spinning icon that says its working... this goes on for minutes
5) I switch to virtual terminal 1 to try and login.  After entering my password the login stalls and eventually times out (60 seconds)
6) I try to ssh into the machine, which also times out.
7) I may have killed the power at this point and repeated steps 1-5 a few times, but eventually I get a login, check /proc/mdstat and realize that the array is re-syncronizing.  Then I let it go for a few hours until it's done.
8) After it re-syncronizes then I can actually login to gdm and get a semi-functioning system (some of the gnome panels didn't come up)
9) Eventually (after your help) I force fsck on reboot and now everything is cool.

Not sure whose responsibility it is, but the fact that they system boots and lets you login even when it can't complete the login while the array is resyncronizing is a usability problem.  Should there be an check in init that checks the array status before proceeded.  Just so that the user should be prevented from proceeding if the system is not ready.  Likewise, init stalls and gives a progress report when it does an fsck on boot.

Anyways, this is resolved for me.  Hope that the discussion is helpful for others.

---

### Post by tgrimley on 2009-09-10
I know you've already marked it as resolved, but I think you bring up some interesting comments.

Your array should be online during resync and responsive (maybe a little slow).  I've never an md raid array as a system partition, so I don't know, maybe it is much worse in that case.  You might still want to check out the smart status on your drives to see if lots of errors are causing the drives to be non responsive.

---

