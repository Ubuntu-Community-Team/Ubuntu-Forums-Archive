---
title: "Monster File Means Failed Drive?"
date: 2010-03-02
forum: General Help
---

### Post by truth is life on 2010-03-02
I recently had a problem with an absolutely gobsmackingly huge .xsessions-error file growing in my /home partition (over 200 GB--the only reason it stopped growing was that there wasn't any room left). So, I deleted it, and then to see what problems had been causing the file to grow so huge, I rebooted the computer to regenerate it. Big mistake.

Since then, I haven't been able to boot. The process hangs when it reaches the step of mounting the /home partition. Luckily, I have my install CD, so I was able to boot into that environment. First, I checked disk integrity--everything was just fine. Then, I tried booting into the liveCD environment. Jackpot! It reports that the bus between /dev/sda6 and itself is timing out when I try to access the former home partition, but I can get into my / partition just fine.

I have just edited my /etc/fstab file to *not* know about /dev/sda6, so hopefully it will boot properly (though of course without any access to the files on /home) soon. If this works, I will update.

But, does anyone else at all know anything about this sort of problem and what I can do to fix it? Regenerating my /home partition on / merely postpones the problem and doesn't actually get me any of my files back.

UPDATE: Well, that didn't work. Actually, it sort of did, but not quite the way I wanted it to. I was indeed able to bypass mounting the /dev/sda6, but I was not able to boot into Xubuntu since the graphical log-in manager failed and none of the ttys started. The failure mode was, however, interesting. It did not merely fail, but instead flickered violently with a frequency of several seconds until I tried switching to one of the virtual terminals (C-M-!, if anyone is interested).

---

### Post by RedRat on 2010-03-02
Odd you should mention this particular problem of an enormous file of 200Gb. On one of my home computers used by my daughter and grandson, all of a sudden it ran out of hard disk space! Long story short, it was a file under Windows/sys32/spooler. There was a file there called spooler.xml and it had grown to 266GB in size. The only way for me to delete the file was to go into Windows in safe mode and delete the file.

Some research on Google, indicated that it might be conflict between MSFT Anti-virus and my other virus program (McAffee). Why and what was writing to that file, I do not know. Obviously, this may not be related to the problem you observed in Linux, but odd that this just happened to me too, different operating system.

---

### Post by truth is life on 2010-03-03
I also had the idea of fscking the affected partition, in case there was some kind of file system damage that had occured (which is my working theory). Unfortunately, it appears that there is some kind of problem communicating with the device, so it isn't working

And I tried booting into my system without /dev/sda6 using the recovery kernel, not the regular one. I assume that wouldn't work any better?

---

### Post by Strongman332 on 2010-03-03
have you tried using the hard-drive utility on a live cd

---

### Post by truth is life on 2010-03-03
> **Strongman332 said:**
> have you tried using the hard-drive utility on a live cd

You mean the disk integrity check? Yes, I mentioned that in my first post. A-ok, it says. So, it's not a hardware failure.

EDIT: And I should mention the "problem communicating with the device" is limited to the /home partition. The / partition works just fine.

---

