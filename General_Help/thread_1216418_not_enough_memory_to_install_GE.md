---
title: "not enough memory to install GE?"
date: 2009-07-18
forum: General Help
---

### Post by langyaw on 2009-07-18
hello Ubuntu experts,
I've just successfully installed Ubuntu 9.04 in my laptop, and I can now dual-boot between it and Vista. in Ubuntu, I downloaded GoogleEarth (a .bin file) and tried installing it (sudu sh <.bin filename>), and it seemed to install, but a window popped up telling me I did not have enough memory to install GE? how could that be? did I make a mistake in installing Ubuntu, in that I should have assigned a bigger space to it? can I correct this within Ubuntu? or, do I have to re-install it and assign a bigger partition space to it? please be gentle with me as I'm a complete newbie "dummy" with Linux.:(

---

### Post by XCan on 2009-07-18
I'm uncertain if by memory they mean disk space or RAM. Could you post the output of

df -h

and

free

---

### Post by langyaw on 2009-07-20
> **XCan said:**
> I'm uncertain if by memory they mean disk space or RAM. Could you post the output of

df -h

and

free

Here are the results of those commands.
COMMAND: df -h
RESPONSE:
Filesystem         Size    Used   Avail    Use%  Mounted on
/dev/sda5         2.3G     2.3G    0       100%   /
tmpfs            1006M       0    1006M     0%    /lib/init/rw
varrun           1006M     104K   1006M     1%    /var/run
varlock          1006M       0    1006M     0%    /var/lock
udev             1006M     168K   1006M     1%    /dev
tmpfs            1006M     504K   1006M     1%    /dev/shm
lrm              1006M     2.4M   1004M     1%    /lib/modules/2.6.28-11-generic/volat
overflow          1.0M      20K   1004K     2%    /tmp
COMMAND: free
RESPONSE: 
           total    used    free    shared    buffers    cached
Mem:     2060016  527472   1532544     0      31744     232144
-/+ buffers/cache:  263584  1796432
Swap:    176672      0      176672

now, what? do I need to re-install Ubuntu 9.04?

---

### Post by irv on 2009-07-20
It appears you don't have enough space on your Linux partition. What you need to do is boot with the Live CD and run off of it. When the desktop appears just do System>Administration>Partition Editor. You can resize your Vista partition down and make your Linux partition bigger. You may want to check to see how much room you have to spare before doing this. Be careful not to make your Vista to small.
I have my Vista set at 148Gig and Linux at 70Gig. I still got 47Gig left on my Linux partition. Here is a couple of screen shots of my system.
[ATTACH]121750[/ATTACH]

[ATTACH]121751[/ATTACH]

---

### Post by langyaw on 2009-07-21
> **irv said:**
> It appears you don't have enough space on your Linux partition. What you need to do is boot with the Live CD and run off of it. When the desktop appears just do System>Administration>Partition Editor. You can resize your Vista partition down and make your Linux partition bigger. You may want to check to see how much room you have to spare before doing this. Be careful not to make your Vista to small.
I have my Vista set at 148Gig and Linux at 70Gig. I still got 47Gig left on my Linux partition. Here is a couple of screen shots of my system.
[ATTACH]121750[/ATTACH]

[ATTACH]121751[/ATTACH]

hi irv,
Thanks.
I reinstalled Ubuntu and when I got to the part where I can assign a partition size for Ubuntu, I tried moving the slider but apparently, Windows has set a limit for this. right now, the partition is being resized, and it is being set at:
Window Vista (loader)(/dev/sda1)=107.2GB
Ubuntu 9.04= 30.4GB
Ubuntu 9.04 (9.04) (/dev/sda5)= 2.3GB
swap (/dev/sda6)= 172.5 MB
Windows Vista (loader) (/dev/sda2)= 9.0GB

I'll see how this goes and inform you of results as they come.

---

### Post by langyaw on 2009-07-21
> **irv said:**
> It appears you don't have enough space on your Linux partition. What you need to do is boot with the Live CD and run off of it. When the desktop appears just do System>Administration>Partition Editor. You can resize your Vista partition down and make your Linux partition bigger. You may want to check to see how much room you have to spare before doing this. Be careful not to make your Vista to small.
I have my Vista set at 148Gig and Linux at 70Gig. I still got 47Gig left on my Linux partition. Here is a couple of screen shots of my system.
[ATTACH]121750[/ATTACH]

[ATTACH]121751[/ATTACH]

OK, I got it right this time, now my problem is NO SOUND! :confused:

---

### Post by XCan on 2009-07-21
No sound where? Everywhere or just mp3s or movies? Have you checked the settings in Volume Control (right click on the speaker).

---

### Post by irv on 2009-07-21
> **langyaw said:**
> OK, I got it right this time, now my problem is NO SOUND! :confused:

Maybe you should start a new thread for this new problem? The title still says not enough memory to install, people will not no you have a sound problem. You will get more help if people know what your problem is now.

---

### Post by langyaw on 2009-07-22
> **XCan said:**
> No sound where? Everywhere or just mp3s or movies? Have you checked the settings in Volume Control (right click on the speaker).

I think I'll have to start a new thread on this problem. there's no sound from Internet radio, no sound from DVD, there's even no sound when Ubuntu starts up and shuts down! but in Windows, my laptop works fine! :(

---

### Post by langyaw on 2009-07-22
> **irv said:**
> Maybe you should start a new thread for this new problem? The title still says not enough memory to install, people will not no you have a sound problem. You will get more help if people know what your problem is now.

hi irv,
I just posted it as a new problem.
regards,
langyaw

---

