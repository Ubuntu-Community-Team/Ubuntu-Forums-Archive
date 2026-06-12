---
title: "Ubuntu 10.10 and XBMC - laggy and high CPU usage"
date: 2011-01-27
forum: General Help
---

### Post by shaundxb on 2011-01-27
Hi all

I am fairly new to Ubuntu and followed a guide on the XBMC site setting up XBMC on Ubuntu 10.10 (using minimal install CD). Everything installed fine, but when I launch xbmc the screen and mouse is very laggy and running a "top" command I can see xbmc.bin is using 98% to 100% of the CPU. Memory usage is normal.

Here are the basic specs of the system

P4 3Ghz
1GB DDR800
Onboard video (not sure what make). I think sharing 128MB of the RAM.
20GB IDE HDD.

I did a bit of searching around and found that the OpenGL settings (for nvidia cards) could be an issue, but im not sure what to change as im pretty sure the graphics chip is not nvidia.

Can anyone help?

Thanks.

---

### Post by angelsguitar on 2011-01-30
Open the terminal, and execute this command:

```
lspci | grep VGA
```

Post the output here so we can see what Video card you have.

---

### Post by drewski3420 on 2011-02-16
I'm in the same boat as the previous poster. Minimal install, trying to get XBMC going. I originally had the same problem as he did (very laggy mouse, etc). 

I did something, honestly could not tell you what it was though, as I've been at this a few hours and have tried every tutorial I can find. Now when XBMC starts up, I get a message "XBMC needs hardware accelerated openGL rendering. Install an appropriate graphics driver."

As far as lspci, I've got: 
```
00:02.0 VGA compatible controller: Intel Corporation 8252/855GM Integrated Graphics Device (rev 02)
```I'm running Thinkpad R51, Intel integrated graphics, which I believe should support OpenGL. I previously had XBMC working over a regular Ubuntu Maverick install, but I thought I could gain some speed by going minimal.

I'm totally out of ideas at this point.

---

### Post by drewski3420 on 2011-02-27
The answer to this question is [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually%20enabling%20the%20Intel%20driver]("https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually%20enabling%20the%20Intel%20driver")

---

