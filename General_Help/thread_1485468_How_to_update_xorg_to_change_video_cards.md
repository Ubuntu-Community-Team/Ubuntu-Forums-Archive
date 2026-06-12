---
title: "How to update xorg to change video cards?"
date: 2010-05-16
forum: General Help
---

### Post by Brent0 on 2010-05-16
I have a video card (Nvidia) in my computer that I want in another computer. I am going to be using the onboard graphics instead. I am running Lucid 32bit. 

When I start up using the onboard graphics, the BIOS screen appears, then I see the normal underscore "_" flashing in the top left corner, but when that is done, my screen turns black and the monitor shuts off. I tried running a live USB and everything was fine so it's not a problem with the graphics card compatibility. I think I have to try booting into the command line and typing 
```
sudo dpkg-reconfigure xserver-xorg
```but ***I don't know how to enter the command line.***
Is that what I have to do or is there a different way?

Thanks in advance. :)

---

### Post by Oasu4g on 2010-05-16
Your system probably still has the graphics driver installed for your Nvidia card, which is causing problems with your onboard graphics. Put the old card back in and disable the driver in the Hardware Drivers GUI. You should be fine after that.

That's what I would do, but there may be a quicker solution.

---

### Post by Brent0 on 2010-05-16
> **A. Tim said:**
> Your system probably still has the graphics driver installed for your Nvidia card, which is causing problems with your onboard graphics. Put the old card back in and disable the driver in the Hardware Drivers GUI. You should be fine after that.

That's what I would do, but there may be a quicker solution.
#-oHow could I forget that?! Thanks for the reply. I'll report back in a few minutes.

---

### Post by Oasu4g on 2010-05-16
Don't worry about it. I've made my share of video card blunders. There was one time I decided to put my better card in another PC and switch back to onboard graphics in the computer that I was working on. I think I spent hours on it, trying to figure out what was going wrong, because I wasn't getting any output from my monitor. I was about to give up and put everything back the way it was when I realized that I still had the Nvidia card plugged into the motherboard...

Of course, that was a while ago. :-\"

---

### Post by Brent0 on 2010-05-16
It worked for the computer that I took the card out of but the one that I put it in is doing the same thing. This time, it can't be a driver issue because there was no driver in use. :(
Any suggestions?

---

### Post by Oasu4g on 2010-05-16
lol. Make sure the monitor is plugged into the right card?

Otherwise, try booting your LiveCD/USB and see what happens.

---

