---
title: "New kernel doesn't boot"
date: 2011-01-03
forum: General Help
---

### Post by Dans564 on 2011-01-03
Ubuntu will not boot when using the newest kernel update.  All I get is a terminal window.  If I use the previous kernel system boots fine.  I'm using the nvidia driver as well, since this seems to be graphics and kernel related.

---

### Post by wojox on 2011-01-03
Did you install your nvidia driver from "Hardware Drivers" or the nvidia site?

---

### Post by Dans564 on 2011-01-03
I installed using Ubuntu's driver utility "additional drivers"

The kernel that works is ```
Linux kernel 2.6.35-22
```
the kernel that doesn't boot is either -32 or -33 i cant remember.  It the one that you are probably using if your system is up-to-date and working.

---

### Post by Dans564 on 2011-01-03
no one else is experiencing thisss??????????

---

### Post by wojox on 2011-01-03
> **Dans564 said:**
> I installed using Ubuntu's driver utility "additional drivers"

The kernel that works is ```
Linux kernel 2.6.35-22
```
the kernel that doesn't boot is either -32 or -33 i cant remember.  It the one that you are probably using if your system is up-to-date and working.

I'm testing 11.04 so it a totally different kernel. Just wait till tomorrow and try updating again. At least you have a kernel to boot into in the mean time.

---

### Post by Bucky Ball on 2011-01-03
2.6.35-24 is known to have issues on some machines. Well documented.

If that's the one you're talking about then this is not unusual.

---

### Post by Dans564 on 2011-01-04
thanks bucky ball, knowing that atleast gives me some closure on the issue.  I guess ill just have to wait it out for some updates.

---

### Post by Dans564 on 2011-01-04
and for any1 else who has the same issue.  Download start-up manager and set the older working kernel as the default boot.  this at least makes it more convenient then having bring up grub os choices and choose every boot.

---

### Post by Bucky Ball on 2011-01-04
> **Dans564 said:**
> and for any1 else who has the same issue.  Download start-up manager and set the older working kernel as the default boot.  this at least makes it more convenient then having bring up grub os choices and choose every boot.

You talkin' 2.6.35-23 or 22? They work. ;) If anyone is having problems with 24, boot one of the others as well advised and picked up by Dan, using the method he/she described, and wait for a fix before updating the kernel. 

My machine works fine on 24, but I am probably the exception (Toshiba Satellite Pro L510). If you have a Broadcom card, ***avoid at all costs updating your kernel to 2.6.35-24!***

For now at least. Just untick it when you are updating. ;)

Edit: Check this link. There is a link to the bug report there:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

---

### Post by Dans564 on 2011-01-04
22 works, 23 doesn't work

---

### Post by Bucky Ball on 2011-01-04
That's your problem. Stick to 2.6.35-22 (for now until the issue is sorted) or try 10.04 LTS. ;)

I was only aware of the problem with 24. You might perhaps check for bug reports regarding 23. That's a new one on me. :confused:

---

### Post by Dans564 on 2011-01-04
I like 10.10 to much to go back to 10.04, I like up-to-dateness (well at least ubuntu "up-to-dateness)

Thanks for the help on the issue though.  
This forum ROCKS :guitar::guitar::guitar:

---

### Post by Bucky Ball on 2011-01-04
Sure does. Enjoy the 10.10 tweaking. One way to learn and nice to see you're game! Post back in new thread with new probs. The kernel issue should be resolved soon anyhow. 

If you have production machines which you can't afford to go down (like meself) = LTS release.
If you're looking to learn, tweak, learn, and tweak somemore = any other release.

Have fun ... ;)

---

### Post by Dans564 on 2011-01-04
> If you're looking to learn, tweak, learn, and tweak somemore = any other release.=me :p

thanks again

---

### Post by Dans564 on 2011-01-04
PS. do I mark this thread as solved or just closed or what?

---

### Post by Bucky Ball on 2011-01-04
See the last entry in my signature below. ;)

Can't close, stays here to aid other users.

---

