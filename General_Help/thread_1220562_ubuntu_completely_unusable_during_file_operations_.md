---
title: "ubuntu completely unusable during file operations and other &quot;intensive&quot; processes"
date: 2009-07-22
forum: General Help
---

### Post by pythonscript on 2009-07-22
Whenever I start a file copy operation (whether to USB or just my local hard drive) or some other mildly intensive operation, like playing music while using a word document and firefox, my ubuntu installation becomes almost unusable. In general, windows freeze up/grey out, programs take 5-10 minutes to open, etc. Why is this happening? I can't pin it to any one application; it happens with all of them! I'm running an hp pavilion dv2700 laptop with 4 gb ram, a 5400 rpm hard disk, and a 2.4 ghz core2duo.

I'm running 32-bit, so I guess only 3 gb of ram, plus a 128 mb nvidia gefore video card. I can barely use my system when this happens (spontaneously, it seems). Please help! It's a shame that Vista gave me better performance than this. Thanks in advance!

EDIT: I'm a newbie, so if I need to post any log files or other information I missed, let me know!

---

### Post by DeMus on 2009-07-22
> **pythonscript said:**
> Whenever I start a file copy operation (whether to USB or just my local hard drive) or some other mildly intensive operation, like playing music while using a word document and firefox, my ubuntu installation becomes almost unusable. In general, windows freeze up/grey out, programs take 5-10 minutes to open, etc. Why is this happening? I can't pin it to any one application; it happens with all of them! I'm running an hp pavilion dv2700 laptop with 4 gb ram, a 5400 rpm hard disk, and a 2.4 ghz core2duo.

I'm running 32-bit, so I guess only 3 gb of ram, plus a 128 mb nvidia gefore video card. I can barely use my system when this happens (spontaneously, it seems). Please help! It's a shame that Vista gave me better performance than this. Thanks in advance!

EDIT: I'm a newbie, so if I need to post any log files or other information I missed, let me know!

+1. I have the same, especially when using unrar. I have 4 cores and only one is used for the program. Still the other three are not usable either. How come? Isn't Ubuntu written for multi-core processors?

---

### Post by darolu on 2009-07-22
With 4GB of RAM you shouldn't have this kind of problems; the first thing I thought is damaged RAM module, boot from the LiveCD and perform a memory test, make sure it is not damaged.

BTW you can use your 4GB with 32-bit Ubuntu, you just need to install the server kernel:
```
sudo apt-get install linux-server linux-headers-server
```
Your video card driver (propetiary) may not work after this though, but installing the manufacturer driver fixes it.

---

### Post by chriskin on 2009-07-22
i have the same problem here, every time i move files, nothing else works at a reasonable speed

---

### Post by DeMus on 2009-07-23
> **darolu said:**
> With 4GB of RAM you shouldn't have this kind of problems; the first thing I thought is damaged RAM module, boot from the LiveCD and perform a memory test, make sure it is not damaged.

BTW you can use your 4GB with 32-bit Ubuntu, you just need to install the server kernel:
```
sudo apt-get install linux-server linux-headers-server
```
Your video card driver (propetiary) may not work after this though, but installing the manufacturer driver fixes it.

Yes, I know it should not do this, BUT IT DOES!!!

It looks like the 4-cores are not used as they should be used. So, when one core is busy the whole computer is busy and I can drink coffee, a lot of coffee.

---

### Post by jerome1232 on 2009-07-23
Does it do it regardless of if your copying the files via Nautilus vs Command Line? I remember I noticed this once when I actually used nautilus to copy files, but I never notice it when using the command line to do it.

Me thinks nautilus has a bug.

As far as using multiple cores it all depends on if the the program is multi-threaded or not. Most programs are but there are some that aren't.

---

### Post by darolu on 2009-07-23
> **DeMus said:**
> Yes, I know it should not do this, BUT IT DOES!!!

It looks like the 4-cores are not used as they should be used. So, when one core is busy the whole computer is busy and I can drink coffee, a lot of coffee.

Yes that's why I think a RAM module (either DIMM or SO-DIMM) can be damaged, causing jumps (of memory) during file transfering. I don't have a multi-core system but I think you can enable/disable the use (or optimization) of multi-cores, you may want to make a separate thread about it and see if someone else can help you. I've seen options to use or not multi-cores on devede for example.

---

### Post by Chemical Imbalance on 2009-07-23
I've noticed this occurs on my Intel chipset laptops (one an Atom, one a Core 2 Duo).

Doesn't happen on my AMD Quad Core desktop however.

---

### Post by Johnny B on 2009-07-23
i think the bug is with ext4
when i first installed jaunty, it would freeze when i deleted something
i've had no problems since i downgraded

---

### Post by pythonscript on 2009-07-23
> **darolu said:**
> 

BTW you can use your 4GB with 32-bit Ubuntu, you just need to install the server kernel:
```
sudo apt-get install linux-server linux-headers-server
```Your video card driver (propetiary) may not work after this though, but installing the manufacturer driver fixes it.

I use nvidia drivers that I selected through the Hardware menu, so would those continue to work? Or would I simply have to re-select them from the menu? Any other downsides to using the server kernel? Would this affect my normal usage in any way (apart from the performance gain of using 4 gb instead of 3)? Thanks!

---

### Post by automaton26 on 2009-07-23
Well, I use Kubuntu 64-bit on a Core i7.

[LIST]
[*]It's not ext4 - it happens with my ext3 partition.
[*]It's not Nautilus - it happens with Dolphin.
[/LIST]

There have been several threads about this, and no definite answer.[http://ubuntuforums.org/showthread.php?t=1150108]("http://ubuntuforums.org/showthread.php?t=1150108")

I tried disabling USB Legacy support in the BIOS, but that broke KDE, even though I restored the BIOS setting immediately :(

To fix that, I had to uninstall and re-install my ATI Catalyst drivers, like this:

[http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")

---

### Post by darolu on 2009-07-23
> **pythonscript said:**
> I use nvidia drivers that I selected through the Hardware menu, so would those continue to work? Or would I simply have to re-select them from the menu? Any other downsides to using the server kernel? Would this affect my normal usage in any way (apart from the performance gain of using 4 gb instead of 3)? Thanks!

No it won't affect your normal usage; the driver installed through hardware menu may not work after installing the server kernel; you probably will need to install the driver you download from nvidia.com, it is very easy to install don't worry; you download it, kill X server (graphic server), install and restart X server. To kill X server and install, you need to close your user session and when you are back to GDM (the log in screen) press Control+Alt+F1, this will show a terminal emulator where you can kill X server with "sudo killall gdm" and then you can install the nvidia driver; you need to do "sudo sh ./nvidia-driver-file" and the installer will guide you, is very simple, the nvidia installer does it all for you, once it is installed you simply start X with "startx" and you are good to go.

---

### Post by pythonscript on 2009-09-05
I went ahead and installed the server kernel, and I haven't had any issues since. My system still runs a bit slow when I copy files (using gnome, not the computer that's listed in my signature) but from the command line, there's no performance degradation and there never was. I'm content with my computer's performance now. Thanks for the help!

---

