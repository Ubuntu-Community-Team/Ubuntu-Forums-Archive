---
title: "Ubuntu 10.10 is slow on Compaq C610"
date: 2011-02-08
forum: General Help
---

### Post by -Strider- on 2011-02-08
Hi guys!
I'm a new to Ubuntu but I love it! I installed ubuntu 10.10 on my desktop and it's running really fast without any problem.

But after I installed on my laptop it's ruining very slowly. I cant figure out the reason.I use Compaq C610. Specs are as follows.


Intel® Core™ 2 Duo Processor T5870 (2.00 GHz, 2 MB L2 cache, 800 MHz FSB)
Mobile Intel® GME965 Express Chipset with IC
500 GB SATA
Mobile Intel® Graphics Media Accelerator X3100 (integrated)

it takes around 1 min to get shutdown while my desktop bootup and shutdown within in few seconds.
Both of the machines have almost same specs.
Please help if u know the something to speed up the machine
Tnx!!

---

### Post by -Strider- on 2011-02-08
Any one?!

---

### Post by -Strider- on 2011-02-08
some one to help please!

---

### Post by Bucky Ball on 2011-02-08
Welcome to the forums.

Running 10.04 LTS faultlessly on that machine (my wife's). I'll have a look later but not sure there were any tweaks required.

It was running 8.04 LTS pretty well previously and I upgraded through the Update Manager to 10.04 LTS which fixed several problems (notably the fan and suspend when the laptop lid goes down). One thing it didn't fix was the long shutdown time. Sped up boot up considerably though.

One thing; a desktop does NOT have the same specs as a laptop. They may have the same amount of storage space and the same amount of RAM but that is where the similarities end. ;)

I haven't tried 10.10 on the C610 as that machine is a uni/games/surfing/emailing workhorse and needs to remain up.

I suggest you try 10.04 unless you're aiming to learn by figuring out the probs. Supported to 2013. ;)

---

### Post by -Strider- on 2011-02-09
Tnx Bucky Ball. Really appreciate Ur help. Heard that 10.04 is faster than 10.10. Hope to try it soon on my lap.:)
Tnx again

---

### Post by -Strider- on 2011-02-12
I m still having the problem. After a fresh install now the system is running faster. But is takes around 45 sec to get shutdown.
Is there any solution for this longer shutdown time??

---

### Post by An Sanct on 2011-02-12
Have you checked the logs?
System -> Administration -> Log File Viewer

There should be some info, that can help you.

---

### Post by Bucky Ball on 2011-02-12
> **-Strider- said:**
> I m still having the problem. After a fresh install now the system is running faster. But is takes around 45 sec to get shutdown.
Is there any solution for this longer shutdown time??

Dunno what that is. I searched for a solution awhile ago but nothing. My wife's 610 is exactly the same; long shutdown. I'm suspecting something to do with the C610 hardware. This problem doesn't exist on my Toshiba laptop, nor the two desktops. Weird. Machine runs great in *every* other respect.

---

### Post by -Strider- on 2011-02-13
Hmm there's no solution for this thing isn't it?
But its ok. I m going to use Ubuntu anyway :D :D

---

### Post by Bucky Ball on 2011-02-13
If it's only slow shutdown and everything else works fine, you're laughing! If I find a fix I'll post it.

Enjoy the new OS and the learning curve. Don't forget to post back with any questions or probs. ;)

---

### Post by Philio on 2011-02-14
Sounds like something is hanging when you try and shutdown the machine. Check dmesg and syslog for the time while your shutting down and look for any errors.

---

### Post by -Strider- on 2011-02-14
How can I check that??

---

