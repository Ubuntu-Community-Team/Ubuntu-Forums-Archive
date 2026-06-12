---
title: "Terminal is all white (9.10)"
date: 2009-11-17
forum: General Help
---

### Post by Hydrofarmer on 2009-11-17
My terminal window is all white!!! what happened?

---

### Post by r3d14l on 2009-12-12
[LEFT]Hi Hydrofarmer,
It sounds like something went wrong in your xorg.conf file possibly.

Are you running an nVidia video card and also missing your window control buttons (maximize, minimize, close)? If your answer is yes to both of these I may have a fix for you.

I just recently broke my /etc/X11/xorg.conf file on two separate machines whilst attempting to setup dual video out.

I was able to remedy my problem by adding the text that is formatted in red below to the section **Section "Device"** in my xorg.conf file.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    [COLOR=Red]Option "AddARGBGLXVisuals" "True"[/COLOR]

Most posts I have found will state that this line belongs under **Section "Screen"**, but at least in my case that did not fix my problem.

If you are unsure how to take a look at your xorg.conf file, open up your blindingly white terminal window and paste in the following command listed in red. Of course you won't be able to see anything, but just bear with me. You could also simply open it with Applications -> Accessories -> gedit, but you will not be able to save any changes you may have to make.

[COLOR=Red]sudo gedit /etc/X11/xorg.conf[/COLOR]
Press Enter
Type in your root password
Press Enter

Within seconds you should get a gedit window that is filled with various sections.

Search for **AddARGBGLXVisuals** and if it doesn't exist put that aforementioned line in the location I discussed earlier, close and save the file and then restart X by logging off and then back on.

Good luck!
[/LEFT]

---

