---
title: "Well, I installed Ubuntu on my Dell laptop"
date: 2009-10-26
forum: General Help
---

### Post by G-Com on 2009-10-26
I experimented with the Live CD for a couple of days and decided to take the plunge tonight and install it.

Pretty slick! ;)  The installation was painless.  Ubuntu* is* a LOT faster than Vista and it was pretty darn fast off the disc.

I solved a problem I was having accessing certain folders on an HFS-formatted external drive: I moved the contents out of the folder.:cool:

I miss all the familiar Mac OS X and Windows fonts and I need to find a way to disable the touchpad when the mouse is plugged in and download VLC and a couple of other things.  But it looks like Ubuntu's got a convert.

I'm certain I'll be back for help.  Allow me to thank you in advance. :)

---

### Post by macaholic on 2009-10-26
Congrats! You've gotten past what I believe to be the hardest part of linux, the initial setup. Now the time comes to get familiarized and have every little thing tweaked the way you want it.
Welcome to the Ubuntu community, enjoy your stay :)

---

### Post by G-Com on 2009-10-26
> **macaholic said:**
> Congrats! You've gotten past what I believe to be the hardest part of linux, the initial setup. Now the time comes to get familiarized and have every little thing tweaked the way you want it.
Welcome to the Ubuntu community, enjoy your stay :)

Ooh... a fellow Maccer.):P  Thanks for the welcome.  It's always a pleasure to talk to a Mac fan. :)-

The built-in movie player is good.  So that solves that.

Would you happen to know:

1.  How to disable the touchpad when the mouse is plugged in.

2.  A good adblocker for Firefox?

3.  Getting a recycle bin icon on the desktop.

---

### Post by Capt. Blackwood on 2009-10-26
I've just told popups no to pop up for that. 

As for the other two...i don't know.


Welcome to the party. I've been here for 2 months...and well, i like it.

---

### Post by macaholic on 2009-10-26
Yay for Macs!

I'm not sure about the touchpad...You could google around and probably find something.
AdblockPlus is by far the best adblocker for Firefox: [http://adblockplus.org/en/installation](http://adblockplus.org/en/installation)

As for the trash can, Go into System>Administration>Synaptic Package Manager, search for "gconf-editor", install it. I don't remember where the sortcut is exactly, but you can just do "Alt+F2" and type in "gconf-editor". Once you've launched it, go to /apps/nautilus/desktop and check the checkmark labeled "trash_icon_visible". You can also enable the other icons as you see fit.
Hope that helps!

---

### Post by Giblet5 on 2009-10-26
> 1. How to disable the touchpad when the mouse is plugged in.

Almost. You can turn the touchpad on/off with commands, and therefore by clicking a launcher.

Use gedit to edit your /etc/X11/xorg.conf file.

Add a section:

```
Section "InputDevice"
    Identifier "Synaptics Touchpad"
    Driver "synaptics"
    Option "SendCoreEvents" "true"
    Option "Device" "/dev/psaux"
    Option "Protocol" "auto-dev"
    Option "HorizEdgeScroll" "0"
    Option "SHMConfig" "on"
EndSection
```

Save that, log off, log back in.

Now, you can turn the touchpad on/off via ```
## Turn it off:
synclient touchpadoff=1 &#65293;&#65293;disable touchpad
## Turn it on
synclient touchpadoff=0 &#65293;&#65293;enable touchpad
```


> 2. A good adblocker for Firefox?

AdBlock Plus works very very well.


> 3. Getting a recycle bin icon on the desktop.

You should have one on the default GUI. It should be on the bottom panel in the corner.

If, like me, you removed that panel, you can right-click the top panel, select Add to Panel, and select the Trashcan applet.

---

### Post by G-Com on 2009-10-27
> **macaholic said:**
> Yay for Macs!

I'm not sure about the touchpad...You could google around and probably find something.
AdblockPlus is by far the best adblocker for Firefox: [http://adblockplus.org/en/installation](http://adblockplus.org/en/installation)

As for the trash can, Go into System>Administration>Synaptic Package Manager, search for "gconf-editor", install it. I don't remember where the sortcut is exactly, but you can just do "Alt+F2" and type in "gconf-editor". Once you've launched it, go to /apps/nautilus/desktop and check the checkmark labeled "trash_icon_visible". You can also enable the other icons as you see fit.
Hope that helps!
I used Ad Block Plus in Firefox for Windows.  (I preferred Safari in OS X.)  I should've looked to see if there was a Linux version.

I think I'll just wait until I have more knowledge of Linux before I tackle the touchpad issue. :eek:   Thank you both for the replies.

---

### Post by G-Com on 2009-10-27
> **Giblet5 said:**
> You should have one on the default GUI. It should be on the bottom panel in the corner.
So that's what that is... :o

---

