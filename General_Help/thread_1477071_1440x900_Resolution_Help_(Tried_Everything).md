---
title: "1440x900 Resolution Help (Tried Everything)"
date: 2010-05-08
forum: General Help
---

### Post by LethalResistanz on 2010-05-08
I made the jump yesterday from Vista to 10.4 Ubuntu Lts.

Everything seems to work except I'm having a heck of a time getting my monitor to use 1440x900 resolution

I have a Acer X191w 19" monitor and a ATI 4830 video card. I'm using ATI/AMD proprietary FGLRX graphic diver.

I've tried messing around with the xorg.conf file but I seem to just be a chicken running around with his head cut off. I've also tried some other stuff in the terminal. 

Sorry if there is a absolute known solution. If there is can you please link me there. From my couple hours a research this seems to be a common problem. 

Thanks.

---

### Post by TheNerdAL on 2010-05-08
Did you update you drivers?

---

### Post by dino99 on 2010-05-08
*** I'm using ATI/AMD proprietary FGLRX graphic diver. ***

big error  ;)

sudo rm -f /etc/X11/xorg.conf

into synaptic: remove/purge it then install xserver-xorg-video-radeon

---

### Post by LethalResistanz on 2010-05-08
> **TheNerdAL said:**
> Did you update you drivers?

Update manager doesn't find anything. And the hardware driver scanner doesn't change anything about the driver.

So I would say it is all up to date.

---

### Post by LethalResistanz on 2010-05-08
> **dino99 said:**
> *** I'm using ATI/AMD proprietary FGLRX graphic diver. ***

big error  ;)

sudo rm -f /etc/X11/xorg.conf

into synaptic: remove/purge it then install xserver-xorg-video-radeon

I did the first command in the terminal and got this.

justin@justin-desktop:~$ sudo rm -f/etc/x11/xorg.conf
[sudo] password for justin: 
rm: invalid option -- '/'
Try `rm --help' for more information.


Did really get the second part about what you said. I'm still new so if you could explain it a bit better? Seems like I'm using a bad driver?

---

### Post by dino99 on 2010-05-08
you may use copy/paste

---

### Post by LethalResistanz on 2010-05-08
Ok I'm a total idiot so bear with me. 

I'm in synaptic. What am I looking to purge/remove? the dirver? or my xorg.conf file?

---

### Post by LethalResistanz on 2010-05-08
So, I removed the old driver. I went into synaptic and found the file you specified. It alreayd had a green mark next to it. I right clicked and selected mark for reinstallion. It downloaded a file and nothing has changed. Do I need to reboot? or was it already installed?

---

### Post by dino99 on 2010-05-08
fglrx removed and radeon installed and xorg.conf removed then reboot

---

### Post by LethalResistanz on 2010-05-08
I think I installed it but now I only have the best res option of 1024x768

With the other driver I had 1280x800 I believe.

---

### Post by LethalResistanz on 2010-05-08
Don't think that diver supports 1440x900. 

Anyother ideas?

---

### Post by RJARRRPCGP on 2010-05-08
I would reinstall and try the radeon driver.

---

### Post by dino99 on 2010-05-08
goto system admin hardware driver, and see if the driver is activated

---

### Post by LethalResistanz on 2010-05-08
Solved!

Thanks for the help but actually it was a stupid thing I just realized.

I'm running with 2 monitors. My main monitor was plugged into the second port on my video card. My second monitor I was using as a TV so I couldn't see the computer screen.

All it was doing was seeing my second smaller monitor as the main monitor since it was in the first port and mirroring the image and max resolution onto my main monitor. 

I switched the monitors on my video card and took it off mirror mode and they both work with max resolution. 

Thanks so much for the help. Though I think it was mainly user error here.

Off to enjoy Ubuntu cheers.

---

