---
title: "Disk error"
date: 2010-02-08
forum: General Help
---

### Post by harakiri on 2010-02-08
I installed Kubuntu karmic (dual boot) on Dell Vostro 1700 few days back. Since then I have had infrequent random hangs. The system stops responding. Sometimes it can keep working for hours and sometimes it hangs after 20-30 mins.
Luckily I managed to get a look at a error message that looked like "IO Error on sda sector 273313995' when I went to console mode by pressing Ctrl-Alt-F1. This message kept repeating in an infinite loop. I had to force a reboot to get my system to usable state.
Also, today morning, I was not able to copy a file from my HDD (linux) to a USB. It again said "IO error".

I did a chkdsk on windows and it came clean. So I am guessing it is a error on one of the linux partitions. So how do I check my linux partitions (/ & /home) for errors??

Thanks in advance

Harakiri

---

### Post by jken146 on 2010-02-08
fsck

---

### Post by Pikestaff on 2010-02-08
Pop in a LiveCD, go to System -> Administration -> GParted, right click on the partition you'd like to check and go to "Check".  Then tell GParted to Apply.

That's the GUI-fied way to do it, you can also use the command line if you wish... [http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html)

---

### Post by john newbuntu on 2010-02-09
Just to elaborate on jken246 mentioned, boot from a liveCD and run:
sudo e2fsck -C0 -p -f -v /dev/sda2
presuming /dev/sda2 to be your linux root directory

If this gives any errors, then run:
sudo e2fsck -f -y -v /dev/sda2

---

### Post by harakiri on 2010-02-09
Hi All,
Thanks for the prompt reply.

Harakiri

---

### Post by harakiri on 2010-02-10
Hi,

It gave me no bad sectors!! I wonder what's happening.

Harkiri

---

### Post by harakiri on 2010-02-13
I reinstalled ubuntu. I have not got any disk errors yet.

Harakiri

---

