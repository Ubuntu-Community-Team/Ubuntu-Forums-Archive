---
title: "unmounting cds"
date: 2006-04-11
forum: General Help
---

### Post by guine on 2006-04-11
I have been having trouble ejecting and unmounting cds from time to time and whenever this occurs and I try to unmount through terminal as root I get a message saying "umount: /media/cdrom0: device is busy".  I was wondering if there were any settings or anything that I could change so that cds automatically unmount when I hit the eject button or at least someway that I could easily figure out what program was using my cdrom so that I could stop that program and then unmount the cd.  Thanks.

---

### Post by akudewan on 2006-04-11
This problem usually occurs when you are still in the directory of the CD. First make sure that you have changed the directory to home or something.

If it still doesn't work, then you can use the "fuser" command to see what program is being used. Probably the "lsof" command could also be used.

---

### Post by bernardfrancois on 2006-04-12
I think the standard behaviour in an operating system should be that the CD gets ejected anyway after pressing the button on the CD-drive. Programs can be programmed to handle that.

Now processes can just 'lock' the CD-drive, which is very annoying if you don't know which process is keeping it busy. I would like to see a break-trough on the mainstream market for Linux, but stuff like this is preventing it. You can't expect all users to be handy with a command-line, I think basic stuff like ejecting a CD should be possible for any user.

---

### Post by dcstar on 2006-04-12
[QUOTE=bernardfrancois]I think the standard behaviour in an operating system should be that the CD gets ejected anyway after pressing the button on the CD-drive. Programs can be programmed to handle that.

Now processes can just 'lock' the CD-drive, which is very annoying if you don't know which process is keeping it busy. I would like to see a break-trough on the mainstream market for Linux, but stuff like this is preventing it. You can't expect all users to be handy with a command-line, I think basic stuff like ejecting a CD should be possible for any user.[/QUOTE]
Any CD which is "locked" is done so for (usually) a very good reason, crap operating systems allow you to eject media even when programs still think that they are there (and still need them).

As far as any user being able to eject a CD, that is usually just a modification to the fstab file.

---

### Post by bernardfrancois on 2006-04-12
Sometimes I wish I could just remove a CD. Yesterday I had an old CD-RW and nautilus just kept trying to read it, totally slowing down the OS for minutes (the time it took to start xterm and kill nautilus).

If there's a bug in an application, keeping the CD busy, you have a problem.

Today I also had a similar problem; I was burning a CD with K3B (with setuid bit set, because acces to sufficient resources needs to be guaranteed not to fail while burning) and I decided to cancel the burning process (just by clicking the cancel button). After that, the system became slower and totally froze. I also couldn't eject the cd. All I could do was resetting the computer by holding the power button for a few seconds...

I think it could be done to eject just like that; it might only require a little additional exception handling in programs that work with CD's.

A good operating system should remain stable at all times, no matter how buggy the applications running on it are...

---

