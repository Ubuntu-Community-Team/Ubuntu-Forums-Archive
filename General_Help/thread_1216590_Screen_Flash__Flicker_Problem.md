---
title: "Screen Flash / Flicker Problem"
date: 2009-07-18
forum: General Help
---

### Post by nadjavox on 2009-07-18
Hi,

I am running Jaunty version of Ubuntu with gnome 2.26.1. I have experienced a screen flicker problem since last year, running fesity on the first install. Since then, I have changed motherboard and video cards, and have reinstalled ubuntu. 

However, the screen flicker problem has not gone away. I have not changed monitors and wonder if the monitor could be the problem. I have a 24 inch lcd topaz s monitor. My video card is an ATI Radeon HD 3600 Series. I've tried running dpkg-reconfigure xserver-xorg. I've also tried changing drivers from the FGLRX 3D-accelerated proprietary graphics driver for ATI cards to the default Ubuntu drivers.

When I go to system->preferences-> display, the refresh rate is set at 60hz and does not offer any other refresh rate options. Changing resolution, turning desktop effects on / off does not seem to help.

Can anyone help?

Thank you in advance!

---

### Post by aj_the_first on 2009-07-18
I've got the exact same problem.  Well, slightly different hardware of course, but still an old ATI laptop card from about two-three years ago.  I had no flicker problem at all in Intrepid Ibex 8.10, but now, with Jaunty, I am having really bad flicker and lines and resizing (it looks like that is what is happening sometimes)
I'm watching this thread for an idea as well.

---

### Post by nightmicu on 2009-07-18
Howdy,

   Just installed 9.04 Jaunty and I am having the same issue - 60 Mhz is the only refresh rate, screen flicker/flash - especially when browsing the web in Firefox, large drop-down menus, etc.

I tried turning off effects, too, and that did not make a difference. Saw in another thread that I should check my hardware drivers - when I go to System > Administration > Hardware Drivers a box pops up saying that "Proprietary drivers are being used to make this computer work properly," listing my Broadcom STI wireless driver. My only options are Deactivate (the wireless driver), Help, and Close. It won't let me see any other drivers.

I am running an Acer Extensa 4420-5963 with an ATI Radeon graphics card. Any help here would be greatly appreciated - first time I have EVER had a copy of Linux work pretty much flawlessly right "out of the box" but the screen flicker/flash just won't do :(

Thanks,

Ben

---

### Post by aj_the_first on 2009-07-18
I think I figured it out gents.  At least for Jaunty Jackalope users.
I went to download the ATI proprietary driver and this is what I got:
Read this
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.8&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.8&lang=English)

specifically this line:
"The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above."

Jaunty is a post February release.
I'm not sure if the driver listed lower in the page will work yet, since my download speed while trying to get it is 800bytes/sec....  yes, that is right UNDER 1KB/SEC!!, so it will take me the rest of the day to get it, but I am trying...
If you guys install it and it works, can you let me know so I don't waste 12 hours downloading the thing?
Thanks
AJ

---

### Post by nightmicu on 2009-07-19
Last night I found "ATI Catalyst Control Center" and "ATI Binary X.Org driver" in the Add/Remove programs list. I downloaded both, rebooted my machine, and was greeted by a black screen with funky distorted bands of color near the top of the screen. Did a force shut down (no GUI loaded) and was greeted by a console when I booted subsequent times. Reinstalled Ubuntu and now I'm not sure what to do - screen flicker and resolution just won't do. Is the ATI Catalyst in Add/Remove Programs the same as the one mentioned previously? Should I install one or both of these .. ?

I am running an Acer Extensa 4420-5963 with AMD Athlon x2 64 bit, ATI Radeon Xpress 1250. The ATI driver site points me to 9.3 when I filled out the fields. I also see that 9.6 is out -- I've seen a lot of posts discussing 9.4 but don't know where to download it.. or if it will support my card. 

Thanks

---

### Post by nightmicu on 2009-07-19
Found [this article]("http://listento.jaketolbert.com/linux/solve-video-flicker-on-jaunty-with-ati-x1250/") while trying to find a solution to the flickering. Went to the list of drivers [here]("http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/") and did not see any for Jaunty. Could some of you more tech savvy users clarify this? Are we supposed to install an older driver (assuming they are older by the name). Also, what would be the correct one for my machine - Acer Extensa 4420-5963 (same as article publisher) 64bit AMD Athlon X2, X1250 graphics, 32 bit Jaunty

Many thanks.. hopefully this is a valid solution

---

### Post by 3rdalbum on 2009-07-19
> **nightmicu said:**
> Are we supposed to install an older driver (assuming they are older by the name). Also, what would be the correct one for my machine - Acer Extensa 4420-5963 (same as article publisher) 64bit AMD Athlon X2, X1250 graphics, 32 bit Jaunty

On Jaunty, the correct driver for the card is the default "ati" driver, or the "radeonhd" driver that is also included with Ubuntu. The ATI Catalyst driver cannot be used on an X1250; it's too old.

---

### Post by aj_the_first on 2009-07-19
> **3rdalbum said:**
> On Jaunty, the correct driver for the card is the default "ati" driver, or the "radeonhd" driver that is also included with Ubuntu. The ATI Catalyst driver cannot be used on an X1250; it's too old.

Yes, I have now realized that the older ATI driver will not work with Jaunty...
However, the default Jaunty driver is what is causing the flicker.  I wanted to try switching to the radeonhd driver, but I don't know how.  Can you help me out?

---

### Post by aj_the_first on 2009-07-20
This was reported as a bug and there is already a fix.
 
See post #22 here:
 
[http://ubuntuforums.org/showthread.php?t=1174943&highlight=screen+flicker&page=3](http://ubuntuforums.org/showthread.php?t=1174943&highlight=screen+flicker&page=3)
 
It worked perfectly for me, and was all too easy.
Hope this helps

---

