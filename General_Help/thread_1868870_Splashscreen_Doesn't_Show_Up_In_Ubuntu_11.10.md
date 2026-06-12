---
title: "Splashscreen Doesn't Show Up In Ubuntu 11.10"
date: 2011-10-24
forum: General Help
---

### Post by rasfl3 on 2011-10-24
Hello fellow Ubuntu users! When booting into Ubuntu 11.10 and shutting down the computer, the Ubuntu splash screen does not show up. Instead I get a strange looking white screen as shown in the image attached. Does anybody know how I can fix this? Thanks!

[ATTACH]205413[/ATTACH]

---

### Post by jo4hnc on 2011-10-24
Ditto that. I posted this symptom a couple of times with no response. Here's the latest post and let's hope we get a response.

[http://ubuntuforums.org/showthread.php?t=1868168](http://ubuntuforums.org/showthread.php?t=1868168)

---

### Post by xianbei on 2011-10-25
what type of computer are you using? i have seen differences in this screen on different devices; it may be a driver thing...

---

### Post by wolfgar on 2011-10-25
set resolution to lower then native support. 

Set size and color depth, check the boot splash box using startup manager. system/administration/startup manager. 

Try 800x600 , works for most.

Then: 

CODE: SELECT ALL
sudo update-alternatives --config default.plymouth

select your boost splash

CODE: SELECT ALL
sudo update-initramfs -u


CODE: SELECT ALL
sudo update-grub2


in that order

Does no good to create splash header and not add it to grub lol. So don't forget to update grub.

I hope this helps.

---

### Post by jo4hnc on 2011-10-25
wolfgar,

My splash shows up about every 10th time I boot or shutdown/restart, so, I don't think it's a resolution or driver problem. The size of my boot splash is 640x480

I'm using Gnome 3 but did run a Unity Support test. Here is the result.

jaycee@jaycee-desktop:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   NVIDIA Corporation 
OpenGL renderer string: GeForce 6600/PCI/SSE2 
OpenGL version string:  2.1.2 NVIDIA 280.13 

Not software rendered:    yes 
Not blacklisted:          yes 
GLX fbconfig:             yes 
GLX texture from pixmap:  yes 
GL npot or rect textures: yes 
GL vertex program:        yes 
GL fragment program:      yes 
GL vertex buffer object:  yes 
GL framebuffer object:    yes 
GL version is 1.4+:       yes 

Unity 3D supported:       yes 
jaycee@jaycee-desktop:~$ 

Additionally, here is the info about the computer.

Processor AMD Athlon(tm) 64 Processor 3200+
Graphics Card GeForce 6600/PCI/SSE2 
OS 64-bit
Memory 3.9 GiB

John C

---

### Post by jo4hnc on 2011-10-25
Well all, I did bump the resolution to 800x600 and rebooted three times and it did seem to fix the problem. The only aberration is that the screen at shutdown is black instead of the purple of the startup splash. wolfgar, thanks for the suggestion. I've spent a bunch of time trying to figure this thing out. A simple fix is a good fix!

I won't mark this as solved as I don't know if it will work for rasfl3 or others having the problem.

Thanks again!!

---

### Post by rasfl3 on 2011-10-27
Hi, I apologize for the late reply as I've had a busy week. The above sort of worked. At start up, the splash screen does show up. When shutting down, the splash screen also shows up but distorted, it's not centered on the screen and there's wavy lines running through the splash screen. Any ideas anyone? I appreciate everyone's help in resolving this issue.

---

### Post by wolfgar on 2011-10-27
>sudo update-alternatives --config default.plymouth

Pick by number and hit enter 

>sudo update-initramfs -u

>sudo update-grub2

Reboot

---

### Post by ssherwood on 2012-02-02
Hiya 

I had this issue with ubuntu 10.10 through to 11.10 and the guide I created for 10.10 works for 11.04 and 11.10.

Here is the link:

[http://ubuntuforums.org/showthread.php?t=1821771]("http://ubuntuforums.org/showthread.php?t=1821771")

---

