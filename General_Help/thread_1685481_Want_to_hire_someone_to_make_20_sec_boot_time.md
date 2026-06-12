---
title: "Want to hire someone to make 20 sec boot time"
date: 2011-02-10
forum: General Help
---

### Post by sunruh on 2011-02-10
I have Ubuntu installed on an embedded PC104 controller. I use it to run one application only. It is ran from a command line and we do not use X. Right now it takes 64 seconds to boot up, meaning customers for our robots will be waiting that long after power before they can begin to use the machine. 
 
Is there anyone reading this forum who is qualified to go through my kernel and remove unnecessary boot commands, and significantly lower boot time? We could ship you a board. 
 
I also need my robotics program to autostart. I have not been able to do that yet.

---

### Post by kidders on 2011-02-12
Hi there,

What board/version of Ubuntu are you using?

The more information you post, the better an idea forum posters will have of where to start (and what's likely to be achievable).

As a general rule, modifying your kernel is unlikely to do much for boot time. What's your impression of where the bottlenecks are at the moment? For example, if you were to divide the startup process roughly into three (power on -> kernel initialisation, kernel initialisation -> init scripts, init-scripts -> login prompt), how much time gets spent in each?

---

### Post by daverich on 2011-02-12
have you considered puppylinux running from flash ram?

Kind regards

Dave Rich

---

### Post by sisco311 on 2011-02-12
[http://www.webupd8.org/2009/04/ubuntu-boot-chart-make-graph-with-your.html](http://www.webupd8.org/2009/04/ubuntu-boot-chart-make-graph-with-your.html)

---

### Post by kerry_s on 2011-02-12
sounds like all you need is the mini.iso, just do the base install & apt-get what ever else you need.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by sunruh on 2011-02-13
[SIZE=3][FONT=Times New Roman]Thanks everyone for the helpful advise.  Dave, I looked at the puppylinux, as well as the mini.iso that Kerry recommended.  Kerry, my board is an AMD Geode, 32 bit, compatible with x86.  There are a lot of versions of mini.iso available for x86.  How do I know which one?  Do I need to try them all?  And where do I find the additional apps I would need to install to the base?[/FONT][/SIZE]

---

### Post by oldfred on 2011-02-13
You should not be using any of the standard desktop Linux systems. 

For liability reasons you have to have a real time system. Some versions of Linux are modified for real time use.

If an operator hits emergency stop you do not want the computer to wait to finish another task, it has to be now.

---

### Post by LinuxDriver on 2011-02-16
I perform professional boot optimizations for embedded Linux systems to  some seconds and even to 560 ms  (  [http://www.makelinux.com/emb/fastboot/](http://www.makelinux.com/emb/fastboot/) )
I can give you some tips.
First of all, have you serial console to your computer?
Have you system boot logs with timestamps?

---

### Post by sunruh on 2011-02-18
I plug a monitor and keyboard directly to the PC104, so no need to go serial.  I think the capability may be there, if required.
 
I do not have system bootlogs with timestamps, to my knowledge.

---

### Post by sunruh on 2011-02-26
Kerry_s, I tried one of the mini.iso systems (the one matching my Ubuntu 8.04 version), and I still get a 65 second boot time, the exact same time the original 8.04 version took.  Any suggestions on that?

---

### Post by sunruh on 2011-03-01
Rich, I tried the Puppylinux today and I get a 1 minute boot time.  (still not fast enough.) It spends about 36 seconds loading disk drives.  It seems that eliminating some of the unnecessary disk drive loading would be a likely place to shorten boot time, if I only knew how.  
 
I don't think I can run from flash RAM because I am powering this equipment down every time.  We do not want to have a battery for battery backed RAM.  So I'm booting puppy from the flash drive.
 
I'm working on connecting to a serial console so I can get some boot log time stamp info.
 
Kidders, my original OS is Ubuntu 8.04.

---

