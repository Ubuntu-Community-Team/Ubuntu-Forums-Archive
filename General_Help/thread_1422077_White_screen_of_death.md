---
title: "White screen of death???"
date: 2010-03-05
forum: General Help
---

### Post by xr4ticlone on 2010-03-05
So I had Ubuntu installed for a little while...but it was on a desktop downstairs and it didn't see my wireless USB.  I finally got one that it would recognize...however after using the internet on Firefox (version that came with 9.10...not on it now obviously) if I open a second view in the browser I get the "White Screen of Death" in about 20 seconds.  In the "White Screen of Death" is a little box that has thin colored lines in it.  Also, it does it even when I'm only in one 'view' and had tried to open up the source for other software downloads.  

Ironically when I did a 'Paw Kettle' and strung a long CAT5 cable down to the desktop from my upstairs router / hub it had done the same thing.  I just assumed that it was due to a conflict with the wireless USB and the wired port.  Ok...maybe assumed is the wrong word...how about prayed?   

Please understand and keep in mind that I have 0 programing background and have no real experience with command lines.  So any help you would be gracious enough to give will have to be for someone just above a tech moron.  

  

Thanks in advance...

Chad

---

### Post by lavinog on 2010-03-05
The first thing I would do is to turn off desktop effects. (system>preferences>appearance>Visual Effects --> off)

Did you do any updates after the install?

---

### Post by xr4ticlone on 2010-03-05
> **lavinog said:**
> The first thing I would do is to turn off desktop effects. (system>preferences>appearance>Visual Effects --> off)

Did you do any updates after the install?

No updates...I'll try the effects thanks!

---

### Post by xr4ticlone on 2010-03-05
> **lavinog said:**
> The first thing I would do is to turn off desktop effects. (system>preferences>appearance>Visual Effects --> off)

Did you do any updates after the install?

No updates...I'll try the effects thanks!

======

Ok...did the update...and then right away...White Screen of Death.

Any more ideas???

---

### Post by lavinog on 2010-03-06
what brand video card do you have?
Did you enable a proprietary driver after installing (like ati/fglrx or nvidia)?

---

### Post by xr4ticlone on 2010-03-06
> **lavinog said:**
> what brand video card do you have?
Did you enable a proprietary driver after installing (like ati/fglrx or nvidia)?

Nope...had not done that.  I have NO idea what the video card is...is there an easy way to see that info in Ubuntu?

---

### Post by flippo on 2010-03-06
```
sudo lspci | grep VGA
``` will give it to you I think, it works on my machine...

---

### Post by xr4ticlone on 2010-03-07
> **flippo said:**
> ```
sudo lspci | grep VGA
``` will give it to you I think, it works on my machine...


Ok...I turned off enhanced graphics...and tried to type in this code...but nothing.

I'm assuming the code should be typed in the format area.

I have an ATI RADEON EXPRESS 200 video card...I booted windows XP to find that.  I did a little google search on this card and ubuntu and it seems like I may yet again have a problem as I have 9.10 installed.

I may have to reconsider my thought process as it appears Ubuntu is more work than I was looking for...I really don't have the time to play with all these things...and the more I go down the road with this the more I realize that it's not just getting past the initial set up.

Let me know if I'm wrong on that.   I just wanted a MORE STABLE OS to put on an old desktop the family could use to check weather, email, internet, and maybe play a game or two on.  Also it is in the kitchen area so my wife and I could monitor the kids web usage as they get more into that.  XP seemed to need a restart every time we tried to use it...even if it was just a day between uses.  

There was also a video editing software that I wanted to use that looked promising.  But unlike XP where it's not stable...Ubuntu seems to be designed for someone with IT experience that I don' seem to have.

---

### Post by lavinog on 2010-03-07
The radeon express 200 is no longer supported by ATI's propritary driver (even on windows)  The problem is that the last version that did support that card will not work in recent versions of ubuntu.
The open source ati driver has come a long way these past couple of months, and although the driver that comes with 9.10 is somewhat stable, it still has some issues.  Hopefully the driver that comes with 10.04 will be rock solid.

Ubuntu is not going to be a replacement OS for everyone.  Gaming is still very weak on ubuntu, and most games require some sort of hack in wine to work.

If you decide to go back to XP, it is understandable...I would say give 10.04 a try when it is released in april.  (The april releases tend to focus on stability, while the october releases focus on new ideas)

---

### Post by xr4ticlone on 2010-03-07
> **lavinog said:**
> The radeon express 200 is no longer supported by ATI's propritary driver (even on windows)  The problem is that the last version that did support that card will not work in recent versions of ubuntu.
The open source ati driver has come a long way these past couple of months, and although the driver that comes with 9.10 is somewhat stable, it still has some issues.  Hopefully the driver that comes with 10.04 will be rock solid.

Ubuntu is not going to be a replacement OS for everyone.  Gaming is still very weak on ubuntu, and most games require some sort of hack in wine to work.

If you decide to go back to XP, it is understandable...I would say give 10.04 a try when it is released in april.  (The april releases tend to focus on stability, while the october releases focus on new ideas)

So here is the million dollar question...is the White Screen of Death due to my ATI video card?  

If so is there a reasonable priced replacement card that IS supported?   I can change out hardware fairly easily...it's the software / command lines that I get into trouble with it seems.  

IF...IF....IF I knew that replacing that video card would fix the issue I'd be willing to do that.  

As for games I mean like Cheese, black jack, little stuff like that...not like high end POV shooters or anything like that.  Pac Man and Space invaders would be more our speed.  :  )

---

### Post by flippo on 2010-03-07
You might be able to get things working without even switching your video card by using a generic video driver, your video will just be slower.  If your never using anything video intense though, it most likely won't matter to you, though.

You may have to do some fancy terminal stuff, but the forums are here to give you support.  I can give you a step by step set of instruction to set up your computer using a VESA video driver, which may work with your card (preliminary google reports are positive).

---

### Post by xr4ticlone on 2010-03-07
> **flippo said:**
> You might be able to get things working without even switching your video card by using a generic video driver, your video will just be slower.  If your never using anything video intense though, it most likely won't matter to you, though.

You may have to do some fancy terminal stuff, but the forums are here to give you support.  I can give you a step by step set of instruction to set up your computer using a VESA video driver, which may work with your card (preliminary google reports are positive).

If you are willing...I'm your huckleberry.  

I really appreciate it.  But before we do this...am I going to be happy with the uptime and reliability Ubuntu after we get this fixed?   Or do I have a way too high view of what Ubuntu will do for me?

Thanks,

Chad

---

### Post by flippo on 2010-03-07
Well, computers can be unpredictable.  They are large, complex machines that can break and have broken on nearly every level.  I can't tell you you'll have an up time of X for Linux or X for Windows.  I can give you my personal experiences.  I set up my system a while ago, and after the initial setup I haven't had any major glitches, other than those caused by my own doing.

I can tell you why I love Linux so much though.  Every time I have a problem, even a little one, if I want I can fix that issue.  All of the information required to do so is freely available. That isn't true of a Windows system.

But enough with my rambling about my love of Linux, heres how to play with your display, just in case you decide you want to give it a try.

Here is a description of your problem, if you don't care what your problem, just how to fix it skip this paragraph:

Xorg, the thing that talks to your drivers and is the very base of your graphical display has been getting smarter and smarter in newer Linux releases.  It now tries to guess what drivers you have and what setup is best for you.  This is great! for most people but for some, Xorg guesses wrong, and thats your issue.  We're going to tell Xorg, though something called a xorg.conf how to set up your display to use a VESA driver, a generic driver that works with nearly all hardware, but is very slow, so not good for people who need graphic intense things.  Now, on to the solution:

From my understanding you don't have a display right now.  You'll have to boot your system into recovery mode and do this all from the terminal (its hard to do without the terminal without a display!).  Once you get your recovery mode prompt up type:```
sudo nano /etc/X11/xorg.conf
```This should be an empty file, unless you've created it yourself.  If there is stuff in it already, you may want to back it up.  Close the editor and enter:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bup
```Now, lets get to editing the xorg.conf.  Here is what you need to get your Xorg running with the VESA buffer:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

After you type that in save and exit (I think ctrl+x) then restart, hopefully your graphics will work.  If they don't we will have to do some debugging.  

This will give you a minimal X setup.  If there are some things you don't like, for example the screen resolution will most likely be poor then we can work to resolve that after your graphic display is working.

If you have any issues please just post them.

---

### Post by maxe on 2011-06-28
Just installed Ubuntu 11.04 and added the recommended updates.

When I click away from windows and back to them, they sometimes turn white and unresponsive. I click back and forth to different windows, slowly, until they come back in responsiveness. It feels like a memory issue or something.

In addition I have this problem:

> If I leave my computer alone for half an hour, when I come back  the screensaver is steady. The mouse moves on it but neither clicks nor  keyboard have effected. I am obliged to shutdown and to reboot.I  have this exact same problem. The screen turns into nothing but a white  display with the mouse cursor. You can move it and click or type but  nothing happens. It's like the whole system vanished and all you have is  a mouse cursor. I have to reboot again. What could be causing this?

---

