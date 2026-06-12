---
title: "How I Fixed My Crasing nVIDIA Problem...."
date: 2010-05-16
forum: General Help
---

### Post by ephman on 2010-05-16
hi,

for the last few releases, starting with 9.04 i've been having serious crashing problems with the nvidia driver.  whether i installed it manually using the latest drivers directly from nvidia, or installing them through the restricted driver option.  after a few hours CRASH.  it's been awful.  and i tried everything from this side to the moon to fix this issue, all to no avail.  no idea why i've even stayed with ubuntu after all these issues.  came from the debian world back in 5.04, and almost moved back a few times.  but i did a clean install of 10.04, and thought i'd give the nvidia driver one last chance... if it didn't work i'd be moving back home to debian (with the suspicion the issue would stay).  

so after i tried the restricted driver and CRASH.  nothing to fix it.  then i thought ok i'll try to use the latest driver from nvidia.  but ran into this error when installing it:

> ERROR: Unable to load the kernel module ‘nvidia.ko’. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release. 

so after googling around i found a fix to this error i was getting during the install:

> sudo nano /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

(remember last space)

sudo gdm-stop
sudo apt-get --purge remove nvidia-*

RESTART

(after this ubuntu boots with some graphical errors like white lines and incorrect resolution)

sudo gdm-stop
sudo apt-get --purge remove xserver-xorg-video-nouveau

RESTART

(after this, ubuntu boots with no graphical errors BUT CANT GET INTO TERMINAL with gdm stopped so cant install nvidia drivers)

So heres the tricky part

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

and you need to comment 'blacklist vesafb' and add 'blacklist vgafb16' (both without quotes)

sudo nano /etc/initramfs-tools/modules

and add 'fbcon' and 'vesafb' (dont forget last space)

sudo update-initramfs -u

sudo nano /etc/default/grub

search for 'GRUB_CMDLINE_LINUX=' and ADD (dont delete) vga=771 or 795 (according to your resolution)

sudo update-grub

RESTART

sudo gdm-stop 

something in these instructions have fixed my nvidia crashing problem.  for the past 2 weeks i've been crash free!!!!  playing hi-def videos, flash, compiz with tons of animations and effects.  really i've tried to push the card to it's limits, and no crashing.  this made me feel confident that i could share this as a 'fix' for my crashing problem.

this is my system setup:
Ubuntu 10.04 (clean install)
Asus m70vn
Intel Duo T9400 2.5GHz
4 gig Ram
nVidia GeForce 9640m GT 1GB
17" wuxga screen


i wish you luck and really hope this helps fix your crashing problem.  i know there are a lot of people out there with this serious issue.  makes ubuntu almost useless.

thanks for the bandwith,

ephman

p.s. i have a pretty decent blog you might like [**_ephman.com_**]("http://www.ephman.com") (shameless plug).

---

### Post by dtfinch on 2010-05-16
I had a different crashing problem (Failed to initialize the NVIDIA kernel module... Screen(s) found, but none have a usable configuration.) with the current proprietary driver, which started after I added a second monitor to my GT 240 and enabled TwinView. One monitor was over a VGA cable, the other over DVI.

About 2/3 of the time it would crash X on startup, and the other times it would work just fine, pretty randomly. I spent a few days messing with it. Figuring it randomly wasn't detecting one of them, and giving up, I tried exporting EDID settings and using the ConnectedMonitor and CustomEDID options in xorg.conf, but all that did was make it crash 100% of the time when specified for both monitors. It'd work if I specified CustomEDID for only one monitor, but then only that monitor would be used.

What finally worked was swapping the positions of my monitors on the desk, and making the DVI one the primary monitor instead of the VGA connected one. It shouldn't have made a difference, but I've been crash free for about 6 boots, hopefully not just luck.

Edit: nevermind. It still crashes, but far less frequently, like 1 in 10 boots.

---

### Post by flakifero on 2010-05-16
ephman: 
I had lots of problems with crashings since 9.04 too, but I'm not sure I've got the same problem as you.
Could you please describe the symptoms of the crashings?
Congratulations about solving your problem, I'll continue investigating. 
Thanks
Sry about my english
Flakifero

---

### Post by ephman on 2010-05-16
hi,

ok the best way to describe what's going:

the screen locks up.  however, my mouse works.  i can move it around.  however it's impossible to grap and drag any windows.  can't cut or paste files.  i'm only able to move my mouse.

hope that helps.

ephraim.

---

### Post by flakifero on 2010-05-16
Well, I just finished typing the instructions you left. Now I'm going to light up a couple of candles and just wait. 
Thanks a lot for your explanation, I think I've tried lots of "solutions" but with not luck yet. 
Which was the cause of the freezes at last?
After doing this the graphics on the computer stay basic, and I couldn't for example enable the visual effects and that stuff. I don't know if at this time i have to install envy or something like that.  Any clues? Maybe I'm trying to fly to high.
Thanks
flakifero


I've installed nvidia driver from nvidia. So crossing my fingers, for the moment effects came back... hope without crashes...

---

### Post by ephman on 2010-05-17
depending on if you have a mobile graphics card, you might want to max out the powermizer option for the card settings.  it will hurt your battery life a tad.  but i've read all over the place that the scaling has been an issue.  i have a mobile card so i max it out.  should have mentioned that before.

---

