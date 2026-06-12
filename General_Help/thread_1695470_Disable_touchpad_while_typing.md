---
title: "Disable touchpad while typing"
date: 2011-02-25
forum: General Help
---

### Post by TuxIsAwesome on 2011-02-25
This is really starting to annoy me, which is sad because I love Xubuntu/XFCE4.

How do I disable the freaking touchpad while I type, every time I even lightly hover my palm over it, it jumps the cursor all over the place.

Can someone help me with this?

---

### Post by rcayea on 2011-02-25
I found this in another post. Maybe it will help:


One problem: There's no option to disable tap-to-click. This is a huge problem with a small keyboard and touchpad because my palm keep accidentally clicking when I type.

I tried adding an xorg.conf with a Synaptics entry with MaxTapTime 0 in both /etc/xorg.conf and /etc/X11/xorg.conf -- did nothing.

I can do it, curiously, with synclient MaxTapTime = 0 from the command line but I don't know how to make it permanent. I have to do it again every time I log in.

=========================================================

To autostart, make a small script out of it (don't forget to set it executable!). Then go to Applications --> Settings -> XFCE 4 Settings Manager. Select Session and Startup. Select Application Autostart. Select Add... and I think you can probably figure it out from there.

Code:
#!/bin/bash

# fix touchpad - turn off tap to click
/usr/bin/synclient MaxTapTime=0

---

### Post by TuxIsAwesome on 2011-02-26
Well that isn't nessesarily the solution i was looking for, i like having tap to click. I just want the touchpad to be disabled while I'm typing.

Its a start though and I will test it when I get home from work today

---

### Post by patchwork on 2011-02-26
You can view the synclient parameters using synclient -l

I believe the synclient variable for touchpad use/disable during typing is TouchpadOff
(I have been toggling it on my system to confirm)

Thus ```
synclient TouchpadOff=1
``` would be the command to use in rcayea's script to disable the touchpad while typing.

EDIT:  You can try adding the line above to your ~/.profile so it is executed each time you log in. Just scroll to the bottomof the file , add the command in and save

---

### Post by TuxIsAwesome on 2011-02-26
I will try all this when I get home. I assume that synclient will work with a macbook touchpad as i use one

---

### Post by gsgleason on 2011-02-26
Install package tpconfig.

Then go to System -> Preferences -> Mouse and then there should be a touchpad tab with options to disable tap mouse clicks and to disable touchpad while typing.

---

### Post by TuxIsAwesome on 2011-02-26
glgleason, those instructions would be great. Except I am using Xubuntu, and I have no intention of installing gnome just to access a feature such as that.

I cant use the command line either, it keeps saying it cant open the PS/2 port, which is weird because my Macbook certainly doesnt have one of them.

---

### Post by PhilGil on 2011-02-26
When I was running Lubuntu, I used the folllowing How To from the Arch Wiki: [http://wiki.archlinux.org/index.php/Touchpad_Synaptics](http://wiki.archlinux.org/index.php/Touchpad_Synaptics)

1. Open the following file as root (this is where the file is located in Lubuntu, you'll have to poke around to find it in Xubuntu): ```
# sudo gedit /etc/xdg/lxsession/Lubuntu/autostart
```2. Enter the following line at the end:
    ```
syndaemon -t -k -i 2 -d
```Here is a description of the parameters (feel free to modify them with your personal preferences): 

-i 2
sets the idle time to 2 seconds. The idle time specifies how many seconds to wait after the last key-press before enabling the touchpad again. 

-t
tells the daemon not to disable mouse movement when typing and only disable tapping and scrolling. 

-k
tells the daemon to ignore modifier keys when monitoring keyboard activity (ie: allows ctrl+left click). 

-d
starts as a daemon, in the background.

---

### Post by patchwork on 2011-02-27
Wow, i wasn't paying attention and promptly repeated the above advice.  My apologies.

---

### Post by poodoopealeoaph on 2011-02-27
I have found that a lot of laptops have a designated hot key for shutting off the touch pad. So, try to look over all of your buttons and see what your hot key may be.

---

### Post by fgmart on 2011-03-19
Thank you gsgleason!  tpconfig totally worked.

---

### Post by celsius1414 on 2011-05-09
For future reference on this topic (which I happened across in a Google search), check out this article:

"Tuning the Macbook touchpad in Linux"

> 
The default synaptics driver settings in Linux are a little wonky, and  are far from the feel of using the touchpad in OSX. I have spent some  (read: too much) time tweaking these settings to a much more usable  config.[http://uselessuseofcat.com/?p=74](http://uselessuseofcat.com/?p=74)

---

### Post by mjhatten on 2012-03-29
FWIW:  The location of the file is correct even in 12.04.  I made the changes recommended in this thread for my netbook and it works great!  Thanks.

---

### Post by mjhatten on 2012-03-29
I should have been more clear.  I made the changes to autostart.  I used "sudo nano" for my text editor.

---

### Post by mörgæs on 2012-03-29
> **mjhatten said:**
> FWIW:  The location of the file is correct even in 12.04.  I made the changes recommended in this thread for my netbook and it works great!  Thanks.

Thanks for posting. It's hard to know when a thread is outdated and when it is still valid.

---

