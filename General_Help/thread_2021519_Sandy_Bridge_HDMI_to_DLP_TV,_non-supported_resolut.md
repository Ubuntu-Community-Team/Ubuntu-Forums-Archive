---
title: "Sandy Bridge HDMI to DLP TV, non-supported resolutions"
date: 2012-07-09
forum: General Help
---

### Post by rage_311 on 2012-07-09
All,

I changed my Mythbuntu HTPC over to Sandy Bridge Celeron G530/H67 based hardware from a Clarkdale i3-540/H55 machine.  I've installed and configured Mythbuntu 12.04 while the machine is connected to a 24" 1920x1080 monitor and things were working fine.  When I move it to the TV/AVR, it boots into Mythbuntu and changes the resolution to 1280x720 @ 60Hz which, apparently, isn't supported by my TV (not true).  The TV just displays a message that says "Not Supported Mode".  I know my TV supports this resolution, as well as 1920x1080 @ 30Hz.  I can change the resolution to 720x480 (remotely, via SSH, using xrandr) and get SOMETHING to display.  The display is all garbled and unusable -- several fragments from different portions of the screen stuck together -- plus, this isn't the resolution I want anyway.

I've tried using gft to generate a modeline for xrandr to use for 1920x1080 @ 30Hz, but when I change to this mode, the TV claims that it's not supported.


Some notes of interest:

Ultimately, I need this signal routed through my Onkyo AVR (TX-SR608 ) that uses my Samsung DLP as the display.  This is what I had my Clarkdale machine's HDMI going into.
1280x720 @ 60Hz worked just fine with the Clarkdale i3-540 via on-chip graphics and HDMI through the Onkyo AVR.
My Linux Mint laptop (Acer with a discrete ATI card and open drivers) can use the TV just fine right now in 1920x1080 @ 30Hz (via Onkyo AVR).
xrandr "Can't open display" unless I specify and use the command "DISPLAY=:0 xrandr".  Seems strange.


What am I missing here?  Thanks in advance for any help.  The WAF is on a steady decline right now... so hopefully someone can help me get this turned around.

---

### Post by dino99 on 2012-07-09
with recent hardware, its a good idea to use also one of the latest kernel (3.5) with the latest graphic driver

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

that said, i've often seen users having trouble with hdmi but due to the cable used. Check your mobo doc about hdmi settings, and maybe grab an other hdmi/adapter cable for testing.

note: as actual kernel directly deal with X, remove xorg.conf if it exist (sudo rm /etc/X11/xorg.conf )

---

### Post by rage_311 on 2012-07-09
Thanks for the advice.  I'll install the 3.5 kernel when I get home this evening.

Is xorg-edgers simply a PPA for the latest xorg drivers (that may or may not get brought into the official Ubuntu repos)?  I haven't used it before and can't find much direct info on it.  If that's the case, it will just contain packages that I already have installed on this machine and I can just add the PPA, apt-get update, and apt-get upgrade?

---

### Post by rage_311 on 2012-07-10
Thanks again for getting me pointed in the right direction.

I initially followed your advice and loaded the latest daily kernel build followed by all of the latest xorg-edgers packages.  This caused issues because, I believe, xorg-edgers drivers are built against specific kernel versions (which is why they include kernels in their ppa).  Booting with the latest daily kernel (3.5.0-999) caused instant lock-ups, so I reverted to the latest kernel that xorg-edgers included in their ppa (3.5.0-3, I think), and that WORKED!  I booted into a mostly functional desktop and MythTV environment.  I was able to set 1920x1080@60Hz as my display mode just fine.


Still a few issues that I may or may not be able to resolve in the near future:

1. MythTV's VAAPI has issues and is really inconsistent.  Sometimes it works, sometimes it locks the machine up.  I think this will be resolved by a combination of MythTV updates and updated xorg intel graphics drivers/libva.
2. In the desktop environment, if I click and drag a window or resize it, it freaks out for a few seconds and boots me out to the XFCE login screen.
3. Any remotely fast motion of a white object (eg move the cursor quickly or fast motion in MythTV) leaves green "ghosting" behind.  No idea on this one...
4. When I pop-up my A/V receiver's OSD, it is displayed with strange pink and green colors -- it's normally black and blue.
5. Generally unstable and causes MythTV to crash frequently.  Fortunately this is a Frontend ONLY.


If anybody has any thoughts on any of these issues, I would love to hear them as this machine is still pretty unusable.

---

