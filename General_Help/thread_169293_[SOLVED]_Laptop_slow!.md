---
title: "[SOLVED] Laptop slow?!"
date: 2006-05-02
forum: General Help
---

### Post by Yv12345vY on 2006-05-02
Hi,

This is a follow up post to my previous post about Ubuntu running painfully slow on my laptop.  I installed Ubuntu on another laptop, a Dell this time (I am hoping to get it to work well on my Alienware) and it worked perfectly fine.  On my Alienware, however, it is slow right from the get go!  It's slow starting with the install - doing a side by side comparison, even switching between menus was very delayed on my Alienware.  any idea why?  Is there something specific I should be looking for?  Could the HDD be a problem (it is the only difference between the two laptops - on the Dell I formatted the entire drive, on the Alienware I created a primary partition of 7gb that I used)??  The Dell is slower than the Alienware but it still outperforms it when it comes to Ubuntu.  WHYYYY?????????:confused: :???: :-k :-#

---

### Post by mandrakethepenguin on 2006-05-02
There are many factors to why it may be slow. 7gb may be insufficent, mine is 52gb primary with 1gb logical swap.  The CD you installed with may be corrupted.  If you used a journaled file system such as ext3,reiserfs,xfs,jfs you may need to specify more space (journaled file systems work better with a lot of space).  And, A VERY common problem,  If your Alienware has the x86 processor architecture (eg: Pentium 4, Intel Celeron), ubuntu installs a linux kernel that works at a minimum for those architectures, the i386 kernel.  If you have a pentium 4, you should be using the linux kernel for i686.  To install it run this command in a terminal ```
sudo apt-get install linux-image-2.6.12-10-686
```

---

### Post by Yv12345vY on 2006-05-02
I'll give it a go although the disk space sounds much more promising.  I'm using ext3, which is what I used on the Dell laptop, and I didn't install the 686 kernel, even when I was running the OS.

---

### Post by Yv12345vY on 2006-05-02
Installing a 686 kernel didn't work...I wonder how useful this was anyways since even the setup was painfully slow...

---

### Post by Yv12345vY on 2007-11-02
This is long overdue but adding "mem=512M" or "mem=768M" to boot parameters solved this problem!

---

### Post by hikaricore on 2007-11-02
Marked your thread as solved and made the title slightly less annoying.  ^_^

---

