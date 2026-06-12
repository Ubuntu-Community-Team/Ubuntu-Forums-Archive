---
title: "XP/Ubuntu Dual Boot, HD not full recognized, Stop Error"
date: 2009-12-02
forum: General Help
---

### Post by bobbygf on 2009-12-02
Bunch of problems here.

I wanted to Dual boot XP and Ubuntu 9.10.

1. when I go to install XP it only acknowledges 131gb. Instead of 1 TB. I have A WD Caviar Green 32mb internal HD.

2. I've installed ubuntu on several different types of partitions. I did it where ubuntu makes equal side by side partitions, I did the free space left partition and I did it where I made my own sized partitions. Regardless of how I do it, when I go to run XP i get a stop error.

stop 0x0000007b (0xF789E63C,0xC000000E,0x00000000,0x00000000)

I'm using

amd 3.4 x4
4 gb ram
asus m4a79xtd

My first install was 9.10 on this build (which worked fine). I wanted to do try the dual boot so I put XP on and then tried to go from there.

basically....i suck at life.

thanks. 

I'm sure I missed some key stuff to mention. i've been at this for days and my brain is fried.

---

### Post by some-what-Gnu-2-networks on 2009-12-02
boot from live cd. Then start Gparted. Delete/resize exsisting partitions and expand the NTFS filesystem to the wanted size.

---

