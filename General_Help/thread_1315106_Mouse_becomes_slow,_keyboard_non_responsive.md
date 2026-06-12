---
title: "Mouse becomes slow, keyboard non responsive"
date: 2009-11-05
forum: General Help
---

### Post by betacortex on 2009-11-05
So I just installed Ubuntu Studio 9.10 and when I login all is fine, but then out of nowhere my mouse will go to the speed of molasses and not click sometimes and my keyboard is non-responsive where sometimes it types and other times it doesn't. If I restart then it comes up perfect again till it starts a little while later.... Help!?!

---

### Post by Grahamca on 2009-11-05
I will look forward to the reply as I have had the same problem.

---

### Post by betacortex on 2009-11-05
Come on guys, please I really want to get this problem solved. Most of the other threads about this have died out and I really want to be able to learn for myself and to be able to help others with this problem in the future.

---

### Post by P4man on 2009-11-05
Do you really need ubuntu studio? Thing is, it comes with the rt kernel which is known to give problems on many machines. If you dont really need that kernel, i would suggest trying a regular ubuntu 9.10 and installing the studio packages on top of it.

unless perhaps studio also includes non RT kernels.. do you see any in the grub menu ?

---

### Post by betacortex on 2009-11-05
I am looking into recording so yes it would be nice to have. I have no idea.

---

### Post by P4man on 2009-11-05
Im not saying it is the realtime kernel, but its a likely culprit, so if at all possible, I would narrow the scope of potential causes by trying a normal ubuntu. If that works, you can add all the studio programs easily by installing the ubuntu-studio metapackage, essentially turning ubuntu into ubuntu studio. Then you will be able to test the mainstream and rt kernels and figure out whats causing it, and perhaps how to work around it.

of course if you have freezes with the regular ubuntu we're back at square one, but the odds seem a lot smaller. 

All that said, lets make sure you are indeed using the rt kernel. Can you open a terminal and post the output of this command:

```
uname -a
```

?

If it shows something like linux-rt-2.6.31.xx then its the rt kernel.

An alternative you can try is installing the regular kernel in studio. Only do this if your system is stable enough to complete the process:

```
sudo apt-get install linux-image-generic
``` 

then in grub bootloader, press escape if needed and select the non-rt kernel.

---

### Post by betacortex on 2009-11-05
I can tell you that I had Jaunty installed then updated to Karmic and everything worked in regards to the mouse and keyboard. I switched to Debian to change things up and then got Studio so I could record in the future... So you're telling me it's the kernel, so basically I'm up **** creek? There's gotta be a work around right?

---

### Post by blackhawkover on 2009-11-05
I don't know if Ubuntu Studio is broken, or there is data error. I did a disk check and it was fine. 
I am in the same boat. I had installed it thinking great things, but after about 2 minutes of the sweet studio desktop, I would open an application, and then it would almost but not quite freeze, able to move the mouse, able to try to close windows, but once they close, the mouse was slow and would not respond to much of anything as far as restarting, etc. Can you get studio with just installing ubuntu 9.10 with downloading studio extras? I would very much like to use studio on this machine as it is one of my better machines. 
Thanks. Love the look and feel so far of 9.10 guys. 
keep it up. 
blackhawkover

---

### Post by P4man on 2009-11-06
Im not saying you cant use studio.. at all. Im just trying to narrow down possible causes. Once we have the cause we can look for  a solution or workaround.

installing a standard kernel will not disable recording capabilities or anything. A rt kernel only decreases latency (or makes it more predictable) which apparently helps some profressional audio recorders but im not sure how critical it is for your use. 

either way, id say try installing the normal kernel, its only 1 command to type and find out if the freezes disappear. Its entirely possible they dont and the problem is elsewhere (videodrivers, bios, whatever)

---

### Post by betacortex on 2009-11-06
I had the RT Kernel and so I installed the generic kernel and all is good but it still kind of pisses me off that the RT is having problems... Thanks though. :D

---

### Post by P4man on 2009-11-07
are you using an nvidia card with nvidia restricted drivers?
If so perhaps you can disable those (system > preferences >hardware driver), so the opensource nv drivers are used instead. then try the rt kernel again.

If you still have those issues please post the output of 

```
dmesg
```

(run that from a terminal)

---

