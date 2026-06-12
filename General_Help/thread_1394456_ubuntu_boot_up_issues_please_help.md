---
title: "ubuntu boot up issues please help"
date: 2010-01-30
forum: General Help
---

### Post by l00l0085 on 2010-01-30
Hi, this is an issue I encounter when I turn on my desktop. I get to the grub screen where it tells me to choose if I want windows or ubuntu. Im using ubuntu 9.10. I see the little ubuntu logo but I never get to a log in screen. When I click on any button this is what I get 

Gave up waiting for root device.   common problems:
-boot args (cat /proc.cmdline)
-check rootdelay= (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/66ff360e-caa8-4442c-9fda-b000deae45ab5 does not exist. Dr 
opping to shell!

busybox v1.13.3 (ubuntu 1:1.13-1ubuntu7) built-in-shell (ash)  enter "help" for a list of built-in commands.

I can boot up windows still but I do encounter issues there as well. While using windows it randomly restarts. This mainly happens when Im playing games on steam but that is not the only time its happened. It also happened when I was streaming videos online. This makes me suspect my video card but I could be totally off. 

Ive been using ubuntu 8.04 for 2 years with no problems what so ever. I bought a new desktop and installed 9.10 and assumed that it would be as flawless and crash proof as 8.04 but it seems that windows is working better then ubuntu and its breaking my heart. Please help because I cant live without my ubuntu. :( 


I have windows xp
NVIDIA GeForce 7600 GT
Pentium(r) Dual-Core CPU E6500 @ 2.93 GHz

If there is any other into you require to help please let me know.


Thanks in advance 



PS I dont know a whole lot about computers so youre going to have to walk me through this all.

---

### Post by Joe Question on 2010-02-11
Hello, had the same problem and found your post while googling for a solutiion :) I googled more and found this:

[http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/](http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/)

It worked for me, hope it helps.

---

