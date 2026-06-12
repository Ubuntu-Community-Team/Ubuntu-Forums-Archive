---
title: "Windows Virtual Machine + Virtual Box OSE Problems"
date: 2011-02-12
forum: General Help
---

### Post by Habeouscorpus on 2011-02-12
I have been trying to install Windows XP SP2 on my Ubuntu 10.10 from the recovery disk that came with my computer. I have Guest Additions and a bunch of other suggested packages installed. I created an .iso and a 10 GB virtual disk. When I tried to install the first time, everything went fine until the actual installation ( quick formatting, setup) and I got a BSOD. A "Page fault in nonpaged area" error appeared. The second time, I opted for the regular formatting, and the computer restarted on me. As in, the host machine restarted. I don't know why, but Virtual Box does that to me. When I ask it to restart the virtual machine, it restarts the host as well! 

Am I missing something? Or should I try with the regular install disk I have?

---

### Post by thomasw_lrd on 2011-02-12
I don't think you can use the recovery disk.  I've never been able to get it to work.  I'm pretty sure you need to use a regular install disk.

---

### Post by Habeouscorpus on 2011-02-12
I've done a full reinstall off that disk before...

I'll try the install disk. Thanks!

---

### Post by thomasw_lrd on 2011-02-12
> **Habeouscorpus said:**
> I've done a full reinstall off that disk before...



Did you do a full reinstall in virtual machine though?  I've tried before, but they are hardware specific in most instances.  I'd like to be able to do that myself.

---

### Post by Habeouscorpus on 2011-02-12
No, it was when I was still using Windows, and had never heard of Linux. 

(I disabled my graphics driver, and couldn't figure out how to get it back...)

---

### Post by thomasw_lrd on 2011-02-12
That's what I was thinking.  I've tried using restore disks, but they don't work.  One option you might try, if windows still exists on a physical partition is to use clonezilla live cd to back it up, and then you can restore it a vm.  That's what I'm trying right now with an existing laptop.  I'll let you know how it goes.

---

### Post by Habeouscorpus on 2011-02-12
I have had quite enough of this. In my attempts to install with an install disc, I have had 3 application lockups, 4 kernel panics, 3 blue-screens, and 3 forced restarts. 

It's like Windows *knows.* 

Thanks for your help guys, but I'm calling it a day. (What was I thinking?)

---

### Post by coldraven on 2011-02-12
Read my post here (#7) [http://ubuntuforums.org/showthread.php?t=1682162](http://ubuntuforums.org/showthread.php?t=1682162)
See if your restore disc  is the same as mine.
Even so it should not be crashing or BSOD, I never had that happen to me.

---

### Post by Habeouscorpus on 2011-02-12
Hrm. That's very interesting. I think I'll try that, thank you coldraven.

EDIT: Holy Carp. I'm using a self-compiled kernel, and was using it for the virtual installation. When I booted into my other, non-self-compiled kernels, it worked flawlessly. I feel like a knucklehead.

---

