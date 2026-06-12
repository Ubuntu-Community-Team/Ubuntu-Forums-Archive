---
title: "GDM Resolution"
date: 2010-10-04
forum: General Help
---

### Post by gunksta on 2010-10-04
I am trying to use a large LCD TV as a monitor for movies, etc.

I have the user set up and working. But, I'm struggling with GDM. I rather miss the days where a few cryptic settings in XORG.conf file made everything work correctly.

I added some lines to /etc/gdm/Init/Default and /etc/gdm/PreSession/Default. In both cases I added:

xrandr -newmode "1360x768_60.00"
xrandr -addmode VGA1 "1360x768_60.00"
xrander -output VGA1 "1360x768_60.00"

The next line is original and is

/sbin/initctl -q emit login . . . . . . 

I'm not sure if I'm not adding the xrandr info to the right files/locations or if my xrandr stuff is wrong. For the user, I just logged in via VNC and changed the resolution. That part was easy.

---

### Post by hkphooey on 2010-10-05
Sounds a bit obvious perhaps but have you tried the Monitors application, which you'll find at
 System > Preferences > Monitors

It basically sits on top of xrandr and does all that stuff for you. For the last year or so its been flawlessly recognising any monitor I plugged into it, including my 32 inch LCD TV. Just hit Detect Monitors, and arrange the internal and external screens how you want them.

---

### Post by gunksta on 2010-10-05
Yep. Works a peach -- for users. It doesn't do anything for GDM, because the XRandr mode settings it uses are attached only to that user. In fact, I used this to figure out which mode setting would work for the monitor. 

At this point -- I know which mode setting to use but I do not know how to make _GDM_ use it. I have the individual user accounts fixed.

Just in case I haven't been clear. When Ubuntu boots up, GDM comes up as a blank screen. The TV informs me that the input is wrong. And that's all.

If I blindly type in the password to the first user, I can log into Gnome and at that point my XRandr mode settings kick in and X works fine.

This is NOT a driver issue. It's a resolution issue (unless you want to argue that the driver should detect the monitor's resolution correctly).

Thanks.

---

### Post by gunksta on 2010-10-05
bump

---

### Post by hkphooey on 2010-10-05
Bump? Pardon me for sleeping ... 

OK, well despite the bump, here's something I tried when my laptop was booting up into the wrong gdm resolution - my screen is 1024 and gdm had somehow picked 1360, which meant all the buttons on the far right were off the screen. 

Not sure if this will help you in your situation, but it might be worth a try. 

First do this
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

Then logout. While you're at the gdm login screen, the gnome appearance window will start and let you change the background and themes. This seemed to fix my resolution problem. 

Now login and remove the file (careful here ...)
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

So now reboot and see if gdm is behaving itself.

---

### Post by gunksta on 2010-10-06
> **hkphooey said:**
> Bump? Pardon me for sleeping ...
This _is_ a support forum and for the OP to bump an active request for support is not against the Code of Conduct for the forum. It happens. Especially when people are still dealing with a problem in a busy forum. I promise, if you stick around you'll see it again. But, you are quite correct - It is OK to get some sleep.

> **hkphooey said:**
> 

Not sure if this will help you in your situation, but it might be worth a try. 


It won't work because I have _no_ screen. To quote myself:
> Just in case I haven't been clear. When Ubuntu boots up, GDM comes up as  a blank screen. The TV informs me that the input is wrong. And that's  all.While I am certainly glad it worked for you, I don't see how Gnome's theme control adjusted your resolution. But, I'm in XFCE right now, perhaps I am forgetting part of the dialog.

Anywho -- The difference is you had something to look at. I don't. It's all inky black goodness when I'm in GDM. I can only login, because I can just use the keyboard. I considered modifying your idea to force GDM to autostart arandr, but that still won't help me because I can't see anything and GUIs are notoriously difficult to work with when the screen is blank. IIRC, the config panel for GDM used to be useful. Now it doesn't do much of anything. I'm rather hoping the push for Gnome 3.0 will pre-occupy the Gnome devs. When they get bored, they seem to enjoy removing useful options and configuration tools from everyone's computer.  :)

I may try wandering into the IRC channel to find out if there are any GDM wizards there. I need to learn how to manipulate GDM's preferences settings to move it away from the default XServer settings. I just need to figure out how to properly edit the files.

---

### Post by realzippy on 2010-10-06
*...I rather miss the days where a few cryptic settings in XORG.conf file made everything work correctly.*

...you could create a xorg.conf by **Xorg -configure**
and add the modeline you need for your desired resolution.


BTW,what does *Xorg.0.log* say?

---

### Post by gunksta on 2010-10-06
Interesting thoughts. I was concerned that creating a xorg.conf file was a bad idea. If that's not a concern, that would be a simple way of dealing with the problem and would be universal to all users, which is really preferable over setting up the same xrandr settings for each different user.

The xorg logs look clean. The computer _thinks_ everything is OK. X is guessing the dimensions of the TV/screen wrong and the resulting output is not accepted by the TV.

If I plug in my 19" LG monitor, everything is fine. If I plug in my 36" LG TV, things get wonky. (I think it's 36". I have the necessary resolutions written down at home that I got from the config system built into the TV so that's all good.) 

Anywho -- The computer doesn't even realize there's a problem.

---

### Post by realzippy on 2010-10-06
*The xorg logs look clean. The computer _thinks_ everything is OK*

Really?
Can the driver read the monitor EDID data?
..guess not,since you have to add the mode with xrandr....
Anyway,creating a xorg.conf and adding the resolution is the way to go..
Let me know when needing further help for this.

---

