---
title: "Random lockups every few hours"
date: 2009-10-07
forum: General Help
---

### Post by pompiechokie on 2009-10-07
I have been using Ubuntu Jaunty on an Acer Aspire One 751h laptop, and I experience near-total lockups unpredictably a few times a day. I can only move the mouse, and nothing responds, and I am forced to hard-reboot the computer when this happens. There is no relevant info in any of the log files, and I can't find any way to reliably reproduce this behavior. I have seen similar bugs to this, but I haven't found a useful solution.

I've been using Ubuntu for two years now, and this is the worst bug I have experienced. This is my second time writing this post -- the first time, my computer locked up while I was writing it. If anyone knows of a solution, please give me some advice.

Thanks.

---

### Post by Zoot7 on 2009-10-07
Why not try upgrading the Kernel to either 2.6.30 or 2.6.31? 
**[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")**

I had terrible issues with the default Jaunty kernel 2.6.28, hosed sound after updating with a kernel patch through the repos, and used to randomly get Kernel panics upon shutting down, and I also got the odd lock up here and there. It seems the problems I was having were related to the kernel rather than Ubuntu itself (based on googling) but I've since installed 2.6.31 and everything is working fantastically again.

---

### Post by Sef on 2009-10-07
This problem could be several things.   The first thing I would check would be the ram.  With an Ubuntu CD (or go into possibly GRUB) and run memtest86.   It will check your RAM.

---

### Post by pompiechokie on 2009-10-07
I tried upgrading to kernel 2.6.31, but now the display simply won't start up. I ran it in recovery mode and everything was fine, but when it tried to start up the display, I got a blank screen. 

I also tried memtest86+ from GRUB, but it said "Error 28: Selected item cannot fit into memory". 

Thanks for the advice, though. Do you have any other tips or suggestions as to how to make either of those solutions work?

---

### Post by pompiechokie on 2009-10-08
I also tried kernels 29 and 30, to no avail. Anyone have any other tips?

---

