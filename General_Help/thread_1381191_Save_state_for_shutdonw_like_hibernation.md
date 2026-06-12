---
title: "Save state for shutdonw like hibernation?"
date: 2010-01-14
forum: General Help
---

### Post by ThePhilosopher57 on 2010-01-14
Hi
 
I would like to save the state of my windows. I use many of them at once for programming. With the hibernation mode, I can do that, it work. I want to know how can I do that if I completely shutdonw the computer.
 
Thanks for the help.

---

### Post by warfacegod on 2010-01-14
Try using suspend.

---

### Post by ThePhilosopher57 on 2010-01-15
umm, I don't remember this option. I'll look and try later at home.

---

### Post by ThePhilosopher57 on 2010-01-15
> **warfacegod said:**
> Try using suspend.
 
 
I don't have this mode. The reason I am searching for something else then hibernation is because I need to restart the pc sometimes, for new software installation for example, and I loose all my work place.

---

### Post by warfacegod on 2010-01-15
Suspend and Hibernation go hand in hand. If you have one you should have the other. I don't think it's possible to do what you want though. When you Suspend or Hibernate, the contents of your RAM (in essence your system state) are moved to the hard drive, specifically the swap partition. When you tell the computer to "wake", it reads that state information and puts it back in RAM. It's like you just paused your computer. I don't think any Reboot actually takes place. It is rare that a new piece of software for Linux needs a Reboot, it's possible you are Rebooting needlessly.

---

### Post by louieb on 2010-01-15
Try System>Preferences>Startup Applications>Options Tab

That may do what you want.

---

### Post by ThePhilosopher57 on 2010-01-16
> **warfacegod said:**
> Suspend and Hibernation go hand in hand. If you have one you should have the other. I don't think it's possible to do what you want though. When you Suspend or Hibernate, the contents of your RAM (in essence your system state) are moved to the hard drive, specifically the swap partition. When you tell the computer to "wake", it reads that state information and puts it back in RAM. It's like you just paused your computer. I don't think any Reboot actually takes place. It is rare that a new piece of software for Linux needs a Reboot, it's possible you are Rebooting needlessly.
 
I was looking for something for these rare situations.

---

### Post by ThePhilosopher57 on 2010-01-17
> **louieb said:**
> Try System>Preferences>Startup Applications>Options Tab
 
That may do what you want.
 
 
This is working but some windows are not as they were. Hibernation is better but I take this one for my reboot.
 
thanks.

---

### Post by NTL2009 on 2010-09-06
Old thread I know, but a search turned it up. I want to do something similar. Basically, I'd like to save the current state of my computer when I want (like using 'hibernate'), but then, I want to reboot (maybe from a different install, maybe the same), work on some other stuff, and then be able to come back to that 'saved state' later.

The way I envision this is, I'd need to specify a file name to store the state (really just a place like the swap space, but unique). Then later when I want to return, some way to point to that file to wake up from. That should bring me back to my 'saved state'.

So basically the same as hibernate, but with options on wake up to choose among one or more separate 'saved state' files. Seems this would be convenient when you use the same computer in a few different tasks. Everything could be set up for each task.

-NTL2009

---

