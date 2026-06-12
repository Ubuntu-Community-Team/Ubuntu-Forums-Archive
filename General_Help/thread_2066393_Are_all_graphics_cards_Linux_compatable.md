---
title: "?Are all graphics cards Linux compatable?"
date: 2012-10-04
forum: General Help
---

### Post by John9721 on 2012-10-04
Hey guys, I am new to the forum and new to Linux. I have about a 6 year old gateway desktop that I plan on putting Ubuntu on to play around with. It needs a new motherboard, processor, and graphics card. I just want a cheap graphics card for now as I won't be gaming or anything. My question is, many of the cards say windows 7 compatable but nothing about Linux. Are they all supported or are their certain ones I should use? Thanks!

---

### Post by lykwydchykyn on 2012-10-04
Compatible as in "Can give you a desktop and not take down your system" -- for the most part, yes.

Compatible as in "All features will work and I can run my choice of desktop environment with no problems"  -- no.

---

### Post by nsturdev on 2012-10-04
John9712,

The short answer is most cards you are going to buy will feature a chipset from NVIDIA, ATI or INTEL.  And MOST cards will work.  Linux has excellent generic driver support.  You can get the aformentioned chipset cards very cheap.  Furthermore, ubuntu has an excellent graphical tool to help you identify your cards proprietary drivers if there are any.

---

### Post by Bashing-om on 2012-10-04
John9721; Majority of cards do work - out of the box- there does exist some cases of finding/installing a driver to work. 

As you are contemplating building a system; The compatibility list will prove informative:
[http://www.ubuntu.com/certification/catalog/](http://www.ubuntu.com/certification/catalog/)

This is my main reference, there are others.

[INDENT]Welcome to ubuntu ! <==BDQ

[/INDENT]

---

### Post by Stonecold1995 on 2012-10-04
Most graphics cards will work, but in the case they don't you may be able to find an open source driver that works (such as nouveau for Nvidia).  And what are you planning on doing with that graphics card?  From my understanding, Nvidia provides GPUs that contain less cores (and thus have lower total processing power), but the cores are more versatile and can do more things (CUDA is vastly superior to OpenCL).  AMD on the other hand has GPUs with many high speed cores, but they are simpler and can't do as much.  But what they can do, they do *very* rapidly (Bitcoin mining, password cracking, etc).

Both Nvidia and AMD have many Linux-compatible graphics cards, but overall I'd recommend Nvidia because they can do the most, unless you have a really small budget in which case I'd say go for AMD.

---

### Post by spaceshipguy on 2012-10-05
Actually getting a card to work can be a giant pain in the a**. The AMD, ATI Mobility Radeon card in my laptop is trying to kill itself by overheating and melting the whole computer.
 
I have manged to get a stable system, but with a loud fan . I installed a life-saving program called Jupiter, which turns off any features that would require my dedicated graphics card. The rubbish little card on the mobo has to do everything instead.

When I first got Ubuntu installed the fan sounded like a jet taking off and the system would emergency shut down because of critical heat issues about once every two hours. I needed to open a terminal and do loads of hacker type stuff to try to get things to the point where my computer was likely to see it through the month.

I'm not sure any of it worked. Jupiter was the only thing that stopped my heat issues.

This machine would therefore be very frustrating for a gamer -(it's just fine for me, I can turn my music up loud to cover the fan noise and the computer can run Blender without having to switch on my expensive graphics card).

I would recommend very careful research, especially as the machines in stores usually have the latest components, and are often not well supported by Ububtu.

When I was Googling for a solution to my issues with graphics cards the blame seemed to me to lie with the Linux kernel itself. Apparently it is optimized for servers and is not intended for home use, and the people who create it aren't really laptop people. 

I love Ubuntu though, and I'm sticking with it. I'm hoping that some kernel update or other will result in my machine suddenly going silent and cool. I've owned the machine for a year and no luck yet :-(.

---

### Post by Stonecold1995 on 2012-10-05
> **spaceshipguy said:**
> Actually getting a card to work can be a giant pain in the a**. The AMD, ATI Mobility Radeon card in my laptop is trying to kill itself by overheating and melting the whole computer.
 
I have manged to get a stable system, but with a loud fan . I installed a life-saving program called Jupiter, which turns off any features that would require my dedicated graphics card. The rubbish little card on the mobo has to do everything instead.

When I first got Ubuntu installed the fan sounded like a jet taking off and the system would emergency shut down because of critical heat issues about once every two hours. I needed to open a terminal and do loads of hacker type stuff to try to get things to the point where my computer was likely to see it through the month.

I'm not sure any of it worked. Jupiter was the only thing that stopped my heat issues.

This machine would therefore be very frustrating for a gamer -(it's just fine for me, I can turn my music up loud to cover the fan noise and the computer can run Blender without having to switch on my expensive graphics card).

I would recommend very careful research, especially as the machines in stores usually have the latest components, and are often not well supported by Ububtu.

When I was Googling for a solution to my issues with graphics cards the blame seemed to me to lie with the Linux kernel itself. Apparently it is optimized for servers and is not intended for home use, and the people who create it aren't really laptop people. 

I love Ubuntu though, and I'm sticking with it. I'm hoping that some kernel update or other will result in my machine suddenly going silent and cool. I've owned the machine for a year and no luck yet :-(.

I have the exact same problem, but with a laptop.  I think for some reason Linux in general simply runs very hot...

---

