---
title: "Programs crash"
date: 2006-03-08
forum: General Help
---

### Post by IYY on 2006-03-08
I just installed Ubuntu on a new machine, and while everything works, there are occasional crashes of programs. I'd just be in the middle of surfing when firefox would close, or gaim, or even nautilus or some applet. It seems to be pretty much random, but it doesn't happen when I'm not using the computer.

Sometimes the whole system hangs and I have to reboot. 

During the installation, the package configuration stage failed and I had no GUI. But after running apt-get install -f everything seemed to install fine. My only unusual hardware is a dual display, and I use the nvidia drivers.

Any idea why this could be?

---

### Post by super on 2006-03-08
i have no idea why this would be happening. can you give some more information?

maybe try launching your programs from a terminal to see what error messages are being displayed when they crash.

or try looking at some of the log files of the crashing programs.

---

### Post by Mustard on 2006-03-08
I would run the memtest at boot up from the grub menu and just eliminate your RAM as the suspect first.  Faulty RAM can make things go pretty wacky sometimes.

---

### Post by maddog39 on 2006-03-08
I think it could also be a RAM/Memory issue, windows used to do that and probably still does when you run out of memory and resources. :D

---

### Post by IYY on 2006-03-09
I had Windows installed earlier, though, and there were never any issues. Lately I also had a couple of crashes that made the whole system hang, including the keyboard (Ctrl+Alt+Backspace doesn't work). I'll try launching a couple of programs from the terminal and see how that goes.

---

### Post by IYY on 2006-03-12
I re-installed the system and this is still happening. Today, a terminal application cashed: wget. Said it was a segmentation fault. This kind of problem would suggest faulty RAM, but I did a memtest and it seems to be alright...

---

### Post by 3rdalbum on 2006-03-13
I don't think a Segmentation Fault means the RAM is bad. There are one or two programs that give me those errors at the same place each time, and I don't suffer random crashes.

---

### Post by Mustard on 2006-03-14
[QUOTE=IYY]I re-installed the system and this is still happening. Today, a terminal application cashed: wget. Said it was a segmentation fault. This kind of problem would suggest faulty RAM, but I did a memtest and it seems to be alright...[/QUOTE]

Ok, well having eliminated RAM as the issue, I guess you have to consider what other hardware could potentially be causing it.  It's a process of elimination really.  For a clean install of Ubuntu, this shouldn't really be happening, so something has to be amiss in either the hardware, the media you are installing from, or some other part of the process of installation.

You could try examining your logs in the /var/log/ folder to see what errors may be occuring in the background too.

---

