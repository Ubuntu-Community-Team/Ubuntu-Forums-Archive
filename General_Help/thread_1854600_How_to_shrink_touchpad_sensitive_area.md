---
title: "How to shrink touchpad sensitive area"
date: 2011-10-04
forum: General Help
---

### Post by Ralph L on 2011-10-04
I am installing lucid on a Compaq Presario 2100 (2195 to be exact).  The touchpad worked with no changes to the lucid system, but the ridges on the edge of the touchpad are super sensitive.  Thus whenever I accidentally brush the edge ridges, the pointer jumps all over the place.  Very much a nuisance!!  I am thinking that maybe I can change parameters in the touchpad driver that will shrink the area where the touchpad is sensitive.  In older versions of ubuntu like gutsy, there were numerous parameters (including Top Edge, Bottom Edge, etc) in a file named xorg.conf.  However, I can't find this file in lucid.

1. Does anybody know how I can change the area of sensitivity of the touchpad?  

2.  Does anybody know where I can find the touchpad parameters that used to be in the file xorg.conf.

Any help appreciated.
Ralph

---

### Post by ajgreeny on 2011-10-04
You could install gpointing-device-settings if it's not already installed and see if that gives you any way to do that, or see also if the command ```
synclient -l
``` gives you any clues.  If it does you may need to use trial and error to get the correct figure to use for the eventual command needed, which will be something like ```
synclient LeftEdge=1752
```that figure having come direct from my own netbook.

---

### Post by Ralph L on 2011-10-05
ajgreeny,

Can't thank you enough.  Synclient not only fixed my touchpad sensitive edge problem, but solved a lot of other touchpad annoyances.  I had never heard of synclient and I didn't know I could make a touchpad behave this well.  My touchpad curses have been reduced by a factor of 10.  Somebody ought to create a gui for snynclient and put it in every ubuntu LiveCD.

The parameters I changed (using this website for directions [http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html) ) were:
 1 ClickTime=100.  Don't know if this did any good, since it is supposed to be associated with tap time.
 2 JumpyCursorThreshold=90.
 3 AreaRightEdge=5800
 4 FingerLow=44
 5 FingerHigh=45
 6 PalmDetect=1
 7 Minspeed=.2

Edit:
Turns out synclient doesn't make permanent changes.  To make changes permanent I used instructions from this site [http://ubuntuforums.org/showthread.php?t=1538147&highlight=save+synclient+settings](http://ubuntuforums.org/showthread.php?t=1538147&highlight=save+synclient+settings).  

Originally Posted by NoBugs! View Post
run:
Code:

sudo gedit /usr/lib/X11/xorg.conf.d/10-synaptics.conf

then find the touchpad section and add these 6 lines to it:
Code:

Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"

    Option "JumpyCursorThreshold" "90"
    Option "AreaRightEdge" "5800"
    Option "FingerLow" "44"
    Option "FingerHigh" "45"
    Option "PalmDetect" "1"
    Option "Minspeed" ".2"
    
EndSection

Save and restart and it will work 
Thank you again.

Ralph

---

