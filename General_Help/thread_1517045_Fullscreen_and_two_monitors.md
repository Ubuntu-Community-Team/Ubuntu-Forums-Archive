---
title: "Fullscreen and two monitors"
date: 2010-06-24
forum: General Help
---

### Post by trldp on 2010-06-24
I use two monitors in ubuntu, but I have some problems with fullscreen applications. Sometimes the fullscreen is 'centered' over the two screens (like wesnoth in the attachment (same problem with e.g. ufoai)).

I want the fullscreen application on one monitor (and something else on the other), like in the (second) attachment.

When I do the following, it works:

[LIST]
[*]Deactivate one screen
[*]Start wesnoth
[*]Quit wesnoth
[*]Activete the second screen
[*]Start wesnoth
[/LIST]
But after restarting, I have to do this again. Is there a way to fix this?

---

### Post by tnt533 on 2010-06-24
You may be able to fix this by adding,

Option    "metamodes" "1920X1200,1600x1200; 1920x1200,NULL" 

to the Section "Screen" area of your xorg.conf configuration file located at /etc/X11/xorg.conf. You will have to replace my resolutions with your desired resolutions that fit your monitor setup. This will make X disable one monitor while playing a full screen game and re-enable it when you exit the game. If you want to be able to use both monitors while playing a game like you stated then you will have to run the game in windowed mode to accomplish that or run two separate xscreens which will pretty much ruin the whole purpose for having two monitors in the first place.

To run your game in windowed mode, check the game's documentation.

To set up your system so it turns off your secondary while playing your game automatically, open a terminal and type the following commands.

this backs up the existing file;
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

this opens it for editing;
gksudo gedit /etc/X11/xorg.conf

then add the line above to the screen section of the file with the needed changes and save the file. Restart X and try playing your game again and see what happens.

As for regular apps like Firefox and what not maximizing across both screens, this is going to have to do with how you have your multi-monitor system set up. More information would be needed. What video card are you running, how many, what driver, etc, etc. :p

---

### Post by trldp on 2010-06-25
Doesn't seem to work, but maybe I have to add something else in my xorg.conf file. Now this is my xorg.conf file:
```
Section "Screen"
    Identifier    "Screen"
    Option "metamodes" "1280x800,1024x768; 1280x800,NULL"
EndSection
```> As for regular apps like Firefox and what not maximizing across both  screens, this is going to have to do with how you have your  multi-monitor system set up. More information would be needed. What  video card are you running, how many, what driver, etc, etc. :razz:My video card Radeon Xpress 200M.
So I suppose I use the 'radeon' driver (but I'm not sure, it is automatically chosen by ubuntu). I use the gnome configuration center to configure the screens.

btw: Firefox works fine in fullscreen mode

---

### Post by trldp on 2010-06-25
I have also noticed that when I use 1024x768 as resolution (in the game). It's not centered (like in the attachment)

---

