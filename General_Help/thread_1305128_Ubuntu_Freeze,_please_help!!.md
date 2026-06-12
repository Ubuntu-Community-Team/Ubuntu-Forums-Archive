---
title: "Ubuntu Freeze, please help!!"
date: 2009-10-29
forum: General Help
---

### Post by ayoubson on 2009-10-29
Hi everyone,
I'm fairly new to Ubuntu and Linux, and enjoying the discovery process!! But one thing that has really caused a lot of problems for me, despite using multiple versions of Ubuntu (including the new Ubuntu 9.10 (64bit) which I installed today resulting in the same problem).

The problem:
The hardware: Computer: HP desktop: 64 bit, AMD Phantom x3, RAM 4G (see below)
                      Printer: Brother DCP 7020
                      Webcam: Microsoft Lifecam VX-1000

I have a new HP desktop which I bought a few months back, its a 64 bit AMD Phantom x3, with Nvidea graphics card (non dedicated), and 4 gigs of Ram.

It works perfectly with Windows, and almost perfectly in Linux/Ubuntu except that every time I plug in my Brother printer via USB or my webcam the computer will either freeze all together or either the keyboard or the mouse will stop working, or the system will freeze and continuous string of letters will be typed across the screen when I try to type something.
 After the freeze, the only way to make the computer work is to reboot or switch the power off. Its a persistent and annoying issue. Just to clarify either the printer ALONE or the webcam ALONE or both together can cause the freeze.
I tried using the latest Ubuntu (32 bit/64 bit), Linux mint, and other distros as well, across the kernel range, the same problem happens.
I tried looking for help on the forums but have not found an answer.

I am hoping to ditch windows all together as I am very happy with Ubuntu and my family also likes it, but this problem has really disheartened me, as I need to use the printer.
Although the printer gets recognized, and can work prior to the freeze. The webcam doesn't get recognized at all, even though running lsusb it gets listed. (Microsoft Lifecam VX-1000).
One other thing even if I unplug the printer or the webcam before the system freezes or mafunctions, it will freeze just the same after a few minutes at best.

Just in case I have attached the lsusb list pic to this thread if needed.

By the way, I love the new Ubuntu, every time I say it can't get better than this, it does!

Thank you very much and sorry for the long thread and I hope by solving this issue we can make Ubuntu even more better than it is already.

---

### Post by hal8000 on 2009-10-29
Yes there's a bugfix on launchpad for this:

[https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/258058](https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/258058)

You will not be able to use this until someone creates a patch.

Its been said before, but never buy hardware from vendors who dont support
linux.
HP, Nvidia , Intel actively supported linux from the word go (as do many other vendors)
so you may have been unlucky with this model.


Here is the Ubuntu HCL for webcams:
[http://www.ubuntuhcl.org/browse/search+webcams?category=33](http://www.ubuntuhcl.org/browse/search+webcams?category=33)

Hope that helps

---

### Post by ayoubson on 2009-10-29
> **hal8000 said:**
> Yes there's a bugfix on launchpad for this:

[https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/258058](https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/258058)

You will not be able to use this until someone creates a patch.

Its been said before, but never buy hardware from vendors who dont support
linux.
HP, Nvidia , Intel actively supported linux from the word go (as do many other vendors)
so you may have been unlucky with this model.


Here is the Ubuntu HCL for webcams:
[http://www.ubuntuhcl.org/browse/search+webcams?category=33](http://www.ubuntuhcl.org/browse/search+webcams?category=33)

Hope that helps


Thank you very much for your reply.
My problem with the printer is not the driver it self, I have found a fix for that, and I am able to use the printer to its full capacity, but the problem is the system freeze that happens when I plug in the printer or the webcam. Any ideas why the freeze happens and how to fix it? Thank you.

---

