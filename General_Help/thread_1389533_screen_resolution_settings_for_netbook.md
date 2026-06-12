---
title: "screen resolution settings for netbook"
date: 2010-01-24
forum: General Help
---

### Post by blur xc on 2010-01-24
I've got a Disney edition Asus EeePC with an xp/9.10 nbr dual boot.

The 9" screen has a native resolution of 1024x600, but in xp it can expand that to 1024x768- either by scrolling the desktop up and down a bit, or by what they call "LCD Compress" mode, where ever thing gets squished vertically a bit to fit 768pixels of info in 600 pixels of space.

My daughter uses it to play games on webkinz.com, and their games pop up on a 800px high non resizable or scrollable window, so there are controls and junk that fall off the bottom that can't be reached unless I'm put it in one of the 768 pixel modes.  That, and with her task bar set to auto hide, she can play games and have a good time.  

So, how do I set up Ubuntu 9.10 to do the same thing?  Right now, the only screen resolution in Ubuntu is 1024x600.

Thanks,
BM

---

### Post by blur xc on 2010-01-25
bump

---

### Post by blur xc on 2010-02-01
Seriously?  No one knows how to do this?

BM

---

### Post by monkeyface766 on 2010-02-02
I want to know as well!

---

### Post by blur xc on 2010-02-08
bump

---

### Post by PhilGil on 2010-02-09
I've kludged together a solution for my eee pc 1000h running Ubuntu 9.10.  I placed two launchers on my desktop, one for enabling 1024x768 scrolling mode and one to return to 1024 x 600 mode.

For the 1024x768 launcher, enter the following in the *Command* text box
```
xrandr --fb 1024x768 --output LVDS1 --panning 1024x768
```Enter the following in the 1024x600 launcher's *Command* text box
```
xrandr --fb 1024x600
```I'm sure there are better ways of doing it, but this method works for me.  I still haven't found a way to enable compressed mode.

---

### Post by blur xc on 2010-02-09
> **PhilGil said:**
> I've kludged together a solution for my eee pc 1000h running Ubuntu 9.10.  I placed two launchers on my desktop, one for enabling 1024x768 scrolling mode and one to return to 1024 x 600 mode.

For the 1024x768 launcher, enter the following in the *Command* text box
```
xrandr --fb 1024x768 --output LVDS1 --panning 1024x768
```Enter the following in the 1024x600 launcher's *Command* text box
```
xrandr --fb 1024x600
```I'm sure there are better ways of doing it, but this method works for me.  I still haven't found a way to enable compressed mode.

Wow... that's awesome, I can't wait to try it...  Thanks!

BM

---

### Post by PhilGil on 2010-02-10
> **blur xc said:**
> Wow... that's awesome, I can't wait to try it...  Thanks!

BM
I saw another thread where you posted that no one had answered your question.  Hope this works for you.

---

### Post by blur xc on 2010-03-01
> **PhilGil said:**
> I saw another thread where you posted that no one had answered your question.  Hope this works for you.

I ended up writing a little script and created a custom panel applet launcher deal to run it to toggle between modes.  Thanks for the help.

In panning mode it behaves a bit goofy - if I pan up too fast it won't go pan all the way to the top and part or all of the top panel is still off the screen.  I need to pan up slowly to get it to go all the way up...   Either way - this is a workable solution.

Here's the script-
```
#!/bin/bash

if [ -z "`xrandr -q | grep 768`" ]; then
    xrandr --fb 1024x768 --output LVDS1 --panning 1024x768
else
    xrandr --fb 1024x600
fi
```

BM

---

### Post by PhilGil on 2010-03-01
> **blur xc said:**
> In panning mode it behaves a bit goofy - if I pan up too fast it won't go pan all the way to the top and part or all of the top panel is still off the screen.  I need to pan up slowly to get it to go all the way up.

It works the same way on my netbook.  Tried out your script; it works perfectly. Thanks!

---

### Post by Jr. on 2010-03-15
I am having an issue with my mouse using this solution. When I go into the panning mode my mouse is offset by about 2 inches. I cannot pan all the way up and clicking selects something 2 inches about where the mouse is. I am using UNR on an acer aspire one and sometimes the settings or preferences window of an application will extend past the bottom of the screen. I was hoping I could just switch to panning real quick to make the changes then go back.

---

### Post by blur xc on 2010-03-16
> **Jr. said:**
> I am having an issue with my mouse using this solution. When I go into the panning mode my mouse is offset by about 2 inches. I cannot pan all the way up and clicking selects something 2 inches about where the mouse is. I am using UNR on an acer aspire one and sometimes the settings or preferences window of an application will extend past the bottom of the screen. I was hoping I could just switch to panning real quick to make the changes then go back.

Don't know about your mouse issues, but I've got a tip that might help with your windows that go off the screen.  You can drag a window around, even way off the screen, if you alt-left click anywhere in the window and drag (not just the title bar)...  


BM

---

### Post by MestreLion on 2010-12-29
> **blur xc said:**
> Don't know about your mouse issues, but I've got a tip that might help with your windows that go off the screen.  ***You can drag a window around, even way off the screen, if you alt-left click anywhere in the window and drag*** (not just the title bar)...  
BM

WOW, YOURE MY PERSONAL SUPER-HERO!!!!!!!!!!!!!!!!!!!!!!

Man, sorry for the caps... but this small vertical space has tortured me for MONTHS.. there are DOZENS of apps and dialogs with functionality i could never reach otherwise.

I was googling to find a tool to allow panning (if theres any)... i was ready to use that "switch-script" (no idea *how* to do that), and then...

You nailed it right in the spot!!! Alt-drag... PERFECT!!!! It completely solves that annoying issue... 

Youre the man... and saved my day!! :D

---

### Post by oldmansutton on 2011-07-16
> **PhilGil said:**
> I've kludged together a solution for my eee pc 1000h running Ubuntu 9.10.  I placed two launchers on my desktop, one for enabling 1024x768 scrolling mode and one to return to 1024 x 600 mode.

For the 1024x768 launcher, enter the following in the *Command* text box
```
xrandr --fb 1024x768 --output LVDS1 --panning 1024x768
```Enter the following in the 1024x600 launcher's *Command* text box
```
xrandr --fb 1024x600
```I'm sure there are better ways of doing it, but this method works for me.  I still haven't found a way to enable compressed mode.


if you're currently in 1024x600 mode....

1024x768:
xrandr --fb 1024x768 --output LVDS1 --scale 1x1.28

1280x1024:
xrandr --fb 1280x1024 --output LVDS1 --scale 1.25x1.71


Basically... 
   dw = desired width
   dh = desired height

dw / 1024 = width scale
dh / 600 = height scale

Hope this helps for anyone who, like me, came here looking for a solution.  This is working to stretch me out to 1280x1024 in a 1024x600 resolution.

Cheers.

---

