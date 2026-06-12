---
title: "Erratic mouse behaviour in Ubuntu 9.10"
date: 2010-06-04
forum: General Help
---

### Post by Shrew on 2010-06-04
Hi,

I installed Ubuntu 9.10 on my PC and after a few days of functioning wonderfully, i started to have this problem where at random times, there occur random automatic (uncontrolled by me) mouse movements and clicks (both left and right clicks) whenever the mouse is moved.  And after a while, the mouse completely freezes, refusing to respond to either movement or clicks.

When the mouse freezes, the keyboard continues to work.  The mouse is restored by restarting the machine or reconnecting the mouse.

The problem doesnt occur if i use just the keyboard.  

A regular feature of this situation is that the 'trash' folder opens in multiple windows, sometimes going on opening till i kill the process. (Which, fortunately, i'm easily allowed to do.)


It is a PS2 mouse: CE 3d optical mouse, model UM2018.   I dont think it is a hardware problem since in the exact same configuration i had windows XP, RHEL 4.0 and OpenSUSE 11.0 at different points of time, running without this problem.  Of these, the Windows ran for many years.  Even in the current Ubuntu 9.10, i didnt have this problem for many days.  It was as though suddenly a virus had attacked my mouse.  

Please help!
Thanks,
Shrew

---

### Post by luceerose on 2010-06-04
Do you know how to edit your xorg.conf file ?

```
gksu gedit /etc/X11/xorg.conf
```
And try replacing the mouse section with either of the following;
```
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```
OR
```
Section "InputDevice" 
    Identifier     "Configured Mouse" 
    Driver         "vmmouse" 
    Option         "CorePointer" 
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2" 
    Option         "ButtonMapping" "1 2 3" 
    Option         "ZAxisMapping" "4 5" 
    Option         "YAxisMapping" "6 7" 
    Option         "Emulate3Buttons" "no" 
    Option         "Resolution" "800" 
EndSection
```
The "vmmouse" driver usually works best for me.

---

### Post by luceerose on 2010-06-04
I looked up your mouse model.
"Resolution" for that particular model may need to be set to 400.

---

### Post by Shrew on 2010-06-08
Hi,

The file /etc/X11/xorg.conf did not exist on my machine.  I created it and added the content suggested by you, and in both cases, saved the file, closed it and restarted the machine.  The mouse erratic behaviour is still there!  :-(   What else should i have done?

Thanks,
Shrew

---

### Post by hodumx on 2011-01-29
I had the same problem to on my touchsmart tx2 running 10.10.  the thing of it is is that after repeated attempts on various forum threads installing and un-installing both certain drivers, pluggins, and Ubuntu itself several times the one thing that worked for me was:

-Do a fresh install, without simultaneous updates and fluendo drivers.  Don't have it hooked up to the net in any way.

-After a fresh install only physically hook up the computer to an Ethernet line, fire up the update manager, refresh, and accept all updates.  Re-start computer.

-Do the required proprietary drivers you need.  Re-start computer.

-Profit.

try avoiding the restricted package extras, and do your patches as necessary, ie when you have to play music but don't have the plugins click on the mp3 file and let Ubuntu guide you from that point  Or when firring up Firefox and you're looking at you-tube let FF give you the suggestions for the pluggins on the top right area.  Worked for me so far and no erratic mouse movements! :guitar:

---

