---
title: "Ubuntu suspend freeze, swap partition and mac like sleep mode"
date: 2012-08-05
forum: General Help
---

### Post by najdorfchess on 2012-08-05
Hi all. I have this issue with my Ubuntu running on my Dell Inspiron 15R laptop. When I suspend my laptop, more often than not the whole laptop freezes without the resume prompt asking for password to login and I have to reboot my machine all over again. I was wondering if others have similar issues on their laptops or if there has been a community discussion leading to a fix. 

My laptop is a Dell Inspiron 15R running Ubuntu 12.04 64-bit
Intel Core i3 processor
8 GB of RAM 


One thing I was thought of was the absence of hibernation mode in ubuntu and I read somewhere that it has been disabled by default on ubuntu 12.04 LTS which is sorta okay since Ubuntu boots really fast anyway. So if I need my work to be there when I goto my computer every morning I just need to put it on suspend mode, but because of the freeze problem I have been experiencing some trouble and the following question arose:

[I]Does swap size has got anything to do with laptop suspend mode? If the swap size is close to RAM size or even lesser does this lead to problems after a long suspend (say an entire night!)??
[/I]

Thirdly, what I really like about macbooks is their power options and how the laptop goes into sleep mode once you close the lid and wakes up seamlessly when you open it up and I do that very often and shuts down my laptop only like once a month! So I was wondering if there is a way to do that in Ubuntu and make it work seemlessly like the mac does. 

So help me out with all the 3 issues. Thanks :)

---

### Post by ahallubuntu on 2012-08-05
I use my Dell Inspiron 1545 with sleep mode as you describe: close the lid and it goes to sleep, open the lid and it resumes.  I'm using Ubuntu 10.04 LTS 32 bit.  At first I experienced freezes about 1/5 times when suspending, but after a bunch of kernel updates, it has gotten extremely reliable.  I suspend/resume my laptop several times a day and it hasn't frozen in months that I can recall.

I have booted 12.04 LTS on my 1545 only a few times and have never used suspend/resume on it, so I can't comment on issues with it.  your 15R is newer than mine, different chipset so different issues.  Your 15R may have been Ubuntu certified; you may google around for issues with it and suspend.  Support varies by the hardware.

If you still have Windows available, I'd recommend updating your BIOS to the latest available from Dell.  This can fix issues like you describe, occasionally.

Yes, Hibernation was disabled by default on 12.04 desktop.  On a recent install (desktop), I re-enabled Hibernation; it was pretty easy but I forget how I did it.  Google for it.

No, swap partition size has nothing to do with suspend, but it is important for hibernation.  If you have 8GB of RAM, you want at least an 8GB swap partition (make sure it is really 8192 MBytes not 8000 Mbytes) for hibernation to work correctly.

---

### Post by najdorfchess on 2012-08-05
Thanks for your reply. How to increase swap size for my existing system? I don't see a way to do it via GParted.

---

### Post by najdorfchess on 2012-08-06
Gentle Bounce ^^

---

