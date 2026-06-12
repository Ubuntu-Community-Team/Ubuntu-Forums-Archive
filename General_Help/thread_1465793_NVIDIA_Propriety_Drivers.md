---
title: "NVIDIA Propriety Drivers"
date: 2010-04-29
forum: General Help
---

### Post by glennlh on 2010-04-29
Hi, after installing the NVIDIA propriety drivers for my 8600 GTS, the loading screen that is shown when booting ubuntu is low quality. Does anyone know how to fix this, thanks in advanced.

---

### Post by limey_rick on 2010-04-29
When you say low quality, do you actually mean low resolution? Sorry if I'm miles off with this, but just in case.....

You need to make a change using the NVIDIA Setting tool. I think this would have been installed when you installed the proprietary drivers and is on the System->Administration menu.

You can also run nvidia-settings from the command line.

---

### Post by glennlh on 2010-04-30
What i mean by this is the loading screen is shown at a low resolution, the resolution of the desktop once its booted is fine.

---

### Post by fterh on 2010-04-30
> **glennlh said:**
> What i mean by this is the loading screen is shown at a low resolution, the resolution of the desktop once its booted is fine.
I get that too. Before installation of Nvidia drivers, the Ubuntu loading screen is high-res, but after installation it is low-res and ugly.

---

### Post by glennlh on 2010-04-30
So its not only me, I wonder if there's a fix for it.

---

### Post by Grenage on 2010-04-30
Isn't that normal?  I mean, the driver isn't actually being used until X has loaded?

---

### Post by Shakz on 2010-04-30
> **Grenage said:**
> Isn't that normal?  I mean, the driver isn't actually being used until X has loaded?

No its not normal. 
In 9.10 my load screen looked BETTER after loading the nvidia drivers (more colors)

Thats not the case in 10.04...been like that all through testing. Thought for sure they would have a fix before release. Guess not.

---

### Post by Kirky_D on 2010-04-30
I get this as well, I thought the nvidia drivers were supposed to have KMS by this release? Not sure where I got that from but it's pretty annoying that the default nouveou driver doesn't have 3D yet, and the proprietary nVidia driver doesn't have KMS. 

So either we have a 3D desktop and a low res boot up, or a nice looking boot, and no 3D. In my opinion it's a no brainer as you only see the boot up for like 20 seconds any way but it would be nice to have a more unified feel, which I thought this release and plymouth were supposed to bring.

---

### Post by sevenflo on 2010-04-30
Same with me. Also, my brightness controls cease to work after I install the NVIDIA drivers.

I posted about it here: [http://ubuntuforums.org/showthread.php?t=1466250](http://ubuntuforums.org/showthread.php?t=1466250)

---

### Post by glennlh on 2010-04-30
Thanks for the reply's after looking into some of the things everyone have said, it seems it isn't possible. As said above ubuntu 10.04 does have KMS (Kernel Mode Setting) but it is only enabled when the nouveau drivers are used and not when the NVIDIA proprietary are used. Looks like we'll have to wait for nouveau 3d acceleration.

---

### Post by dino99 on 2010-04-30
all your troubles are due to the nvidia driver, note that ubuntu devs make great job to provide you all with nice built-in nvidia packages working out of the box.

you dont want them, so stop whining  :lolflag:

first: sudo rm -f /etc/X11/xorg.conf 
then
with synaptic, remove/purge all the installed nvidia packages
check you only use official repo (no ppa or exotic repo) and update from main server ( into synaptic)

next step:
install nvidia-current, nvidia-current-modaliases, nvidia-common

reboot
now nvidia-current might be activated (system -admin-hardware driver)

---

### Post by TwiStEr55 on 2010-04-30
thats exactly what we are talking about ... this thread is about the ubuntu supported nvidia prop. drivers, that make plymouth look bad, whereas it looks fine with nouveu but has no compiz support ...


right now its either 3d and compiz vs. nice boot up screen with plymouth

---

### Post by cascade9 on 2010-04-30
> **TwiStEr55 said:**
> thats exactly what we are talking about ... this thread is about the ubuntu supported nvidia prop. drivers, that make plymouth look bad, whereas it looks fine with nouveu but has no compiz support ...


right now its either 3d and compiz vs. nice boot up screen with plymouth

Shouldnt be that hard a choice IMO. I admit my bias, bootscreens, meh. I perfer the old 'lines of text'.

---

### Post by 3rdalbum on 2010-04-30
During 10.04's development, it was actually worse. First, with the Nvidia driver you got a purple, text-based bootup screen; it was like a textual rendition of the high quality Ubuntu screen and I found it quite funny.

The current "non-KMS" splash is actually the second graphical one they tried, and it's nicer than the first (and less humourous than the textual one).

---

### Post by batfink10 on 2010-04-30
I haven't tried it yet, but I came across [THIS]("http://ubuntuforums.org/showthread.php?t=1446132") thread which might fix it.

---

### Post by inso_741 on 2010-04-30
[this]("http://ohioloco.ubuntuforums.org/showthread.php?t=1446132") might help :P

---

### Post by Kirky_D on 2010-04-30
> **batfink10 said:**
> I haven't tried it yet, but I came across [THIS]("http://ubuntuforums.org/showthread.php?t=1446132") thread which might fix it.

I tried that (but I found it elsewhere) with a resolution of 1920x1080 and my monitor had an out of range issue. Wouldn't even display grub. So.. be careful if you try that out.

---

### Post by glennlh on 2010-04-30
I've tried the guide and it made no difference for me. Thanks.

---

### Post by gwi on 2010-05-03
I tried it (set resolution to 1920x1200), and it fixed the bootup screen. It even fixed the text terminals (tty1-6), which where also affected by this problem (went down from ca. 246 columns x 75 rows to 80 columns x 30 rows).

I haven't measured it yet, but my feeling is that scrolling in the tty's is a lot slower now, than it was without the nVidia proprietary drivers. If someone knows how to fix that...

---

### Post by frappe1 on 2010-05-03
I had the same problem at bootup when trying to use anything other than noveau. I can't get either official or repoed NVIDIA drivers to work on a GT260 no matter what I do. To make matters worse, X freezes up every couple hours.

I put in a bug report along with several others, so I hope the devs will be able to fix this soon.

---

### Post by niite on 2010-05-03
I only had luck with the proprietary 173 driver for my dual nvidia 260m's -- still have some performance issues, could be that.  Not sure.  I'd go through the hassle of installing the latest driver from Nvidia but might wait a few weeks to see what kinda updates come out for this distro.

---

