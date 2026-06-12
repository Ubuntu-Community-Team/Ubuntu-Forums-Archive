---
title: "Text problems?"
date: 2009-08-16
forum: General Help
---

### Post by CoolAngelz on 2009-08-16
I was using Fedora before but have had some problems getting a lot of things to work on it, so my friend told me to try Ubuntu.  I didn't seem to notice it when I first used the livecd, but after installing it I'm noticing a little problem, mostly with text areas.

There are times when some of the text that should be black turns white, or partially white.  It happens in Firefox, the menu's, the date/time, icons, almost anywhere there is text.  I hope someones able to help me fix this, cause I can't use it like this.  Its more than a little annoying having text seem to disappear all the time.

---

### Post by Nate Shoffner on 2009-08-16
You can set the background color and fore color in Appearences.

---

### Post by CoolAngelz on 2009-08-16
It's not that.  Not all the colors change, they flicker between white and black.  Usually if I put my mouse over the menu or highlight the text, it changes back to black.

---

### Post by Wim Sturkenboom on 2009-08-16
Can you please provide some details of your hardware (most interesting are make and model of video card and monitor).
Can you also indicate if you installed drivers for the video card and the version of Ubuntu.

---

### Post by CoolAngelz on 2009-08-16
No drivers were installed, it was a fresh install of ubuntu and it also does it while using the live cd.  I just popped my fedora live cd back in and it isn't having the problem, which makes me think it is ubuntu related, possibly with desktop effects even tho I turned them off.  My graphics card is an ATI AIW Radeon 9600XT, the monitor I'm not sure of the model number but it is a Medion brand.

---

### Post by Wim Sturkenboom on 2009-08-16
I suggest that you install the ATI drivers. How is another question as you haven't answered the question which Ubuntu you're using.

Further I leave it to the people who have experience with ATI.

---

### Post by CoolAngelz on 2009-08-16
I'm a little cautious installing ATI drivers, the latest ones either don't compile right or require certain settings that I don't know about, cause everytime I tried to install them before it would make my linux boot up to a black screen.  If theres a work-around for ATI drivers, I haven't looked yet, but I didn't think it would be that since it doesn't happen in Fedora/Mandriva.  I'm using Ubuntu 9.04.

---

### Post by sideaway on 2009-08-16
Don't install the FGLRX drivers, the current ones are incompatible with any radeon card that doesn't start with HD.

You want the Open source radeonhd drivers. I battled with my x1400 for quite a while... Unsure if the stock Ubuntu ones are these, I haven' done a fresh stock install of Ubuntu in nearly 2 years.

---

### Post by CoolAngelz on 2009-08-16
I'm installing a fresh Ubuntu right now and I will try the open source radeonhd drivers.  Hope it works.

---

### Post by martinbaselier on 2009-08-16
If the problem persists, please post the output of:
glxinfo | grep render

and sudo lshw -c video

---

### Post by CoolAngelz on 2009-08-16
Well I'm having larger problems than the flickering text now after spending more than 5 minutes inside Ubuntu.  It happens in my local install and the live cd.  After a varying amount of time, the system stops responding to mouse clicks/keyboard input, the mouse will still move but has a "lag" effect.  After leaving the system for several minutes (hoping it was just thinking), it doesn't solve itself and has to be rebooting with the reset button on the computer.  I managed to download the drivers, but every time I try to spend any amount of time in the system to install them, it does that.  I've never had this problem with other distros so I don't think it's my computer.  My temperature during these times went from 118F to 150F which makes me think its video related as well.

---

