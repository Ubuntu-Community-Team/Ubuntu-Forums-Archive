---
title: "Can't boot (after Windows 7 Service Pack 1 update)"
date: 2011-03-02
forum: General Help
---

### Post by Bob Enzo on 2011-03-02
I have my computer set up to dual boot Windows 7 and Ubuntu.
I did Windows Update and installed Windows 7 Service Pack 1.
Then I went to Ubuntu and it worked fine. I also did some updates there and it told me to restart so I did.
Then I tried booting to Ubuntu but it says something like "... not found..." for less than a second (so it was really hard to read and I am not entirely sure what it said) and it goes back to the boot screen again. 
I select Ubuntu again but the same thing. 
Windows works fine but I just can't boot to Ubuntu any more.

Any suggestions?

---

### Post by wilee-nilee on 2011-03-03
That windows update did mess with the MBR so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Bob Enzo on 2011-03-03
Wait wait wait.
So what exactly do I have to do?
Do I have to burn something to a CD?
I installed using wubi so I am not entirely sure.
Is it possible to do it with a thumb drive?

---

### Post by bcbc on 2011-03-03
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem2, solution1. After you get it booting, apply the Permanent Fix.

---

### Post by Bob Enzo on 2011-03-04
I don't have any spare CD's around and my bios does not support booting from USB.

---

### Post by bcbc on 2011-03-04
Some users reported spontaneous booting (if that happens run the Permanent Fix before shutting down).
Some users found that running chkdsk helped (My computer, right click on Drive, Properties, Tools, Check disk for errors, Fix automatically.... reboot and make sure you let the check disk run).

If those don't work, then you can use [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) to recover important data. 
Otherwise an Ubuntu CD is required - and it's not a bad idea to have one of these anyway as a rescue disk.

---

### Post by Bob Enzo on 2011-03-04
I wasn't lucky enough to get a spontaneous booting.
chkdsk didn't do anything.
Problem 2 Solution 2 of yours worked.
Thanks

---

### Post by bcbc on 2011-03-04
Ok but don't forget you still need the Permanent Fix or it will happen again - and usually overcopying the wubildr doesn't work the second time.

---

