---
title: "Lots of Problems Installing Dapper"
date: 2006-06-05
forum: General Help
---

### Post by JaredG on 2006-06-05
Alright, so, I downloaded the Ubuntu 6.06 - Alternate - AMD64 ISO and burned it to a CD. I popped the CD in.. I chose to install the OEM version. When it went to the black screen... it wouldn't go past 'Booting Kernel. . .'.

 I restarted, repeated the process, it worked. I installed a 7.0gb partition onto my drive with the already partitioned 73.0 gb partition of Windows XP. Everything went fine.. until it finished and it was time to start up. It would not mount the  root file system. I re-installed THREE times, all the same result.

Extra info: I set the boot flag on the 7gb partition to yes, if it matters.

Thanks in advance!

---

### Post by JaredG on 2006-06-05
I just thought of something. Would getting the ubuntu 6.06 - desktop - amd64 make any difference? And also, would getting the i386 maybe fix the problem since I'm moving from 64 bit to 32 bit?

---

### Post by rko618 on 2006-06-05
just a thought

your 7gb partition... are you letting ubuntu automatically partition that space for you?  If you do, it should make it into 3 different partitions: boot, root, and swap.

---

### Post by JaredG on 2006-06-05
I manually edited the partition tables myself. 1x 7gb ext3 and a 533kb swap.

---

### Post by [LvN]N3misiS on 2006-06-05
533kB !!!?? there is your problem then that is far too small a swap partition to have. Generally your swap partition should be 2 -> 3 x the ammount of ram you have (within reason).

---

### Post by JaredG on 2006-06-05
Maybe I got the numbers wrong. I didn't create the swap... linux did that. All I created was the 7gb ext3. But can we at least move onto the real problem here?

Update: I got lucky, and it mounted the root file system. But when I went to log on, it said username or password was wrong..soo.. what the hell. I've re-installed SEVEN times now. I'm getting tired of this.. lol. 

Note: It only mounted the root file system that once, it won't do it again anymore.

---

### Post by JaredG on 2006-06-07
Dump

---

### Post by Ivan Matveich on 2006-06-07
(a) Yes, use the "desktop" version of the installation disc.
(b) Let the installer erase and repartition the whole disk automatically...

---

### Post by kingsidy on 2006-06-07
just choose the partition you want to use using the desktop cd. I could not install with the alternate cd. the desktop cd worked for me

---

### Post by JaredG on 2006-06-08
I can't get the desktop CD to boot the kernel. It won't work.

---

### Post by djsroknrol on 2006-06-08
Check your ISO...sounds like it might have been burned incorrectly.

---

### Post by JaredG on 2006-06-08
I checked the CD using the supplied "cd-checker" on the disk.... nothing wrong with it.

---

