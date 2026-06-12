---
title: "Ubuntu unbearably slow on Celeron 2.4 Ghz"
date: 2006-02-22
forum: General Help
---

### Post by hdagelic on 2006-02-22
Hi,

Yesterday i had an idea to install a couple of linux computers for a classroom at our faculty - but it can't be done because of something I've never seen before!

The basic installation lasted for about half an hour or even longer and it looks to me that it was about 3 times as long as other installations (the problem was in the package installation part which I guess needs processor power). But the worst part came when I tried to install MS office with Crossover. I managed but it takes about 15 seconds for Word to launch. Firefox launches in 6 seconds, OpenOffice Writer in 15-20 seconds. When synaptic (apt) is installing packages you barely run anything, sometimes applications wouldn't even launch!

The wierd thing is that the processor seems to be the narrow neck - in all cases it jumps to 100% and remains 100% until the program is launched. But when looking at the processes and add all usages up it is below 40% (if that is even possible)!

RAM: 256 MB
PROCESSOR: Celeron 2.4 GHz
CHIPSET: i848
HD_DMA: on

Can it be something to do with the kernel and it's inefficient job scheduling because of some hardware problem? It looks like it's wasting time. I'm not using some well known motherboard (First). Is there something I could look at?


Thank you.

---

### Post by lamego on 2006-02-22
I would start by looking the system log : "sudo dmesg" .

---

### Post by yota on 2006-02-22
Hi,

I'm another unlucky owner of a 2.4Ghz Celeron, and I'm running ubuntu on it too.
I think only one thing can be said about that cpu: it really sucks, thanks intel!
It has 24x clock multiplier, 100Mhz memory bus and only 128kb cache memory: so it's a super-clocked processor that spends most of his life awaiting data from ram...
I have slight better performances, probably because i have 512mb of ram, and maybe I've gained something (just a bit) compiling the kernel, from ubuntu's linux-tree sources, with p4/celeron optimizations.

By the way I've only performance issues, so if i try to launch multiple appications simultaneously (even while I'm installing updates) it takes forever, but does everything i told.

The algebric problem in cpu usage, AFAIK is simply explained: 100-system time%-user time%=idle time%
So in your case you have 60% of cpu time for system calls and I/O wait and 40% for user tasks, that's not abnormal when a program starts (expecially with slow disks).

---

### Post by hdagelic on 2006-02-22
I did an experiment at home and took out some memory so there was 256MB left. It is memory! It doesn't work well with 256MB! Processor keeps jumping to 100% (when Synaptic is downloading packages for example) and when there is 512MB the processor is at 3-4%

I guess that the Ubuntu's kernel is optimized for 512 MB or more? Or does it realy need all that memory?

---

### Post by yanik on 2006-02-22
Swap memory is slow.  more ram=less swap.  512MB is the sweet spot for gnome. If you run a lot of apps at the same time on a lot of virtual desktop, I suggest 1GB to substain great performance.

I have 10 virtual desktop with OOo, evolution, plenty of firefox, about 10 gnome-terminal, and a couple of vnc/rdp sessions and I saw a great performance gain by upgrading to 1GB.

Yanik

---

### Post by lamego on 2006-02-22
If you dont have enough memory, the kernel itself will spend a lot of cpu swapping process in and out of memory. This will waste your cpu time. If you have such a small memory sized system you should use a less demansing WM (like icewm) or no WM at all :p

---

### Post by jvnn on 2006-02-22
My new install also suffers from being slow.
My machine is a good chunk faster P4 2.6/800 w 2X512MB on i865 chipset.
Still...internet was _way_ slower than my similar machine running win2k.
Reading here got me to put in firefox 1.5 and it's liveable, but still not how I want it.
For now I'm going to hold off on big changes while I get a bit up to speed.
Future looks like a lighter wm for me.
If there's some obvious speedups I should be trying that are tweaks versus big changes like wm, I'd be glad to hear about them.

Thanks - Joel

---

### Post by dcstar on 2006-02-23
[QUOTE=jvnn]My new install also suffers from being slow.
My machine is a good chunk faster P4 2.6/800 w 2X512MB on i865 chipset.
Still...internet was _way_ slower than my similar machine running win2k.
Reading here got me to put in firefox 1.5 and it's liveable, but still not how I want it.
For now I'm going to hold off on big changes while I get a bit up to speed.
Future looks like a lighter wm for me.
If there's some obvious speedups I should be trying that are tweaks versus big changes like wm, I'd be glad to hear about them.

Thanks - Joel[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

Also do a forum search for "enable DMA" and "disable IPv6"

---

### Post by hdagelic on 2006-02-23
[QUOTE=lamego]If you dont have enough memory, the kernel itself will spend a lot of cpu swapping process in and out of memory. This will waste your cpu time. If you have such a small memory sized system you should use a less demansing WM (like icewm) or no WM at all :p[/QUOTE]


I really don't think that 256MB is so little. This was the standard 4 years ago. XP :-# runs just like that on 256MB. Gnome existed 10 years ago and then it ran on 64MB. So I guess I should need 5GB if I want to run it 5 years from now [-( 

I just don't understand the virtual memory entries in "system monitor", look:

firefox-bin --- 92.1 MB
gnome-cups-icon --- 37.5 MB
nautilus --- 29.9 MB
clock applet --- 21.4 MB
trashapplet --- 20.3 MB
mixer applet --- 20.1 MB
wnck applet --- 19.6 MB

etc.



How come that memory usages are so high? On XP firefox takes 30MB or so and here it is 92 MB! How come? :confused:

---

### Post by jvnn on 2006-02-23
Thanks David!
I will be trying all of your suggestions.

I tried updating the driver for my ati 9600 vid card and have some confusion about what I just did.  I seem to have some very fine dark horizontal scan lines that I don't remember from before and the text scrolling isn't real good.  I need to read up on installing and configuring the driver, then I'll probably wipe and re-install everything (since I'm too new to figure out what isn't right, what to change, etc).  Then I can get back a known starting point and try to be more deliberate and comprehending what I'm doing.  (yeah right)
I'm making notes and will try to suggest some changes to the beginner level wikis based on what I've bumped up against so far.

I also suspect that I'm only scratching the surface and it will probably be a while before I end up with a system  I'm happy with and understand enough to maintain without wiping every time I get confused.

This should all probably be over in installation & upgrade help I guess...

newbie hell - doncha love it.
-Joel

---

### Post by jvnn on 2006-02-25
OK, all is done.
Putting in the smp kernel helped a good chunk.
I'm not sure how much enabling dma helped.
disabling IPv6 seems like it helped the most.

Thanks, great!

---

