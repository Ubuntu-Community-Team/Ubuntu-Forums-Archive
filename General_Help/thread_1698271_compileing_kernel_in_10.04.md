---
title: "compileing kernel in 10.04"
date: 2011-03-02
forum: General Help
---

### Post by tzenda on 2011-03-02
so I am wanting to compile my own kernel to see if i can get my laptop to run a lill better. I found the how too's to do the compile, but what I want to know is.. what is the most complete way to find all the hardware and such that is in my laptop so i can build all the support into the kernel that i need and leave out EVERYTHING i dont need.

i figured lspci is a start but there has to be more info somewhere to find the exact needs of the laptop.

---

### Post by oldos2er on 2011-03-02
**lshw**

---

### Post by tzenda on 2011-03-03
thanks, is there anything else that has other info?

---

### Post by oldos2er on 2011-03-03
Well, there is **sysinfo** and **hardinfo**, among others.

---

### Post by NightwishFan on 2011-03-03
You can use "make localmodconfig" before you do the compile to automatically deselect all of the modules not used in your machine.

I did this once, it did not seem to improve performance at all, and there is a chance you will not have a module you need in the future.

I have a tutorial for compiling a kernel (if you are not into the ck patches, just ignore the section in the middle about adding them). The end result of the tutorial is a ready made debian package to install the kernel. :) Please ask if you have any questions about it. (Though make localmodconfig should work in just about any way you choose to compile a kernel, it is not specific to my method).

---

### Post by tzenda on 2011-03-04
well i do have a question about makin a new kernel. How do i go about removing the stuf i already did. 

What i mean is i followed one tutorial but it ended up not working because it was to old and didnt have all the steps for 10.04. so i found another one that i started to work through but i am thinking i want to get rid of all the stuff from the failed attempt because the new tutorial is a lill different and is actually using a more up to date kernel package.

where is the tutorial that you made? I will give it a look through.

I have compiled a kernel before, but it was many years ago for debian. Back then there were about half as many kernel options to go through and i found all the info i needed rather easily. I am wishin i kept my notes from the to workthrough now. When I made that kernel it made a big difference to that old computer. I am not expecting such a big difference this time because this laptop is a bit more up to date.

Just kind of doing it to get back into the way linux works.

---

### Post by NightwishFan on 2011-03-04
Wow I am so sorry I got distracted and just neglected to edit in the link. Again my apologies.

[http://ubuntuforums.org/showthread.php?t=1637004](http://ubuntuforums.org/showthread.php?t=1637004)

Note the tutorial is for Maverick, but it works in lucid as well (you just have to pay attention to the text that is coloured to see what you may need to change to 2.6.32) Also as before, if you do not want the ck patches, just ignore the steps about downloading and patching them. (I actually do not use them any more either)

I also always use my own custom kernel, though I leave in all the modules. Some changes I make are:

[LIST]
[*]300hz
[*]Full Preemption
[*]Preempt Tree RCU
[*]SLAB
[*]Optimize For Size
[*]Deadline IO Scheduler
[/LIST]

---

### Post by lithopsian on 2011-03-04
Don't be afraid to take out hardware support.  Just mark it to be built as a module.  Any module that you see getting loaded when your machine boots (lsmod) you can set to build into the kernel.

Unnecessary modules don't slow down your machine (hardly), they just make the compile longer and take up a bit of space.  You can take out stuff you know you'll never need.

Go slowly with the more dubious stuff.  Always keep a workable config so you can go back easily.  Always keep a stable kernel in Grub so you can boot even when you build a garbage kernel.

Tweak initramfs too.  The default contains dozens of modules that most people will never need and is about 5 times as big as necessary.  Only affects boot of course.

---

