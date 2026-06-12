---
title: "Help!  System won't go beyond splash screen"
date: 2011-04-07
forum: General Help
---

### Post by djetch on 2011-04-07
Hello all!  I'm rather tired and frustrated at this point, so I turn to those wiser and more experienced than myself.  At the recommendation of a friend I attempted to switch from GNOME to xfce4.  Well I'm guessing that either I did something wrong or my video driver issues (nVidia) followed me and compounded.

This all started when I tried to add a second monitor to my HP Pavillion DV9000 laptop which at the time was running Ubuntu 10.10 just fine.  I loaded the nVidia drivers per the system's request and the monitor's display became distorted.

So I did some googling, some tinkering and some installing, reinstalling and removing of various config bits, packages and what not.  All with out fixing the problem.  By the time I was done my GNOME interface was even a little messed up.  My 4 workspaces had disappeared and anything I opened did not have bar and opened up on top over the system tray at the top.

(1 key thing to point out is that in my googling I found a patch for xserver-xorg-core that was suppose to resolve the monitor issue specific to nVidia & 10.10.  I found this through the Ubuntu site if I remember right.)

So, frustrated, I decided to just press on with changing the desktop manager.  I was hoping that it was reload or over write whatever is messed up causing my growing issues.

Nope.

Now the machine boots, I get a splash screen that says "xubuntu" (with a little mouse) and it just sits there until I do a control-alt-delete at which time it will reboot and do it all over again.  I have tried reloading grub 2 from the live CD with no change.

I'm at a loss.  I don't mind reinstalling but there are some config files that I would like to get off of the machine to prevent me from having to redo my work.  Right now though I am going to bed.

---

### Post by djetch on 2011-04-07
As I lay in bed last night drifting off to sleep I realized the true genius and use of the LiveCD.  I could merely mount it and copy of fresh clean files to replace what I had messed around with.

...trying now...

---

### Post by searchfgold6789 on 2011-04-07
Didn't the config-file-changing actually create more problems rather than fix them?
I would install xubuntu fresh and then apply the patch from the Ubuntu site.
If that doesn't work (which it probably will), *then* I would start to mess with configuration files.
I hope this approach works if you try it!
 - search

---

### Post by djetch on 2011-04-07
So, in using the LiveCD I was about to mount to existing file system, access it and remove my xorg.conf file.

BOOM! Not more stuck at the splash screen but I'm still having some issues with the actual desktop (i.e. windows don't have borders, no virtual desktops, show desktop button doesn't work).  So now I'm working to re-install the xserver-common and xserver-xorg-core packages.

---

### Post by djetch on 2011-04-07
> **searchfgold6789 said:**
> Didn't the config-file-changing actually create more problems rather than fix them?
I would install xubuntu fresh and then apply the patch from the Ubuntu site.
If that doesn't work (which it probably will), *then* I would start to mess with configuration files.
I hope this approach works if you try it!
 - search

Sorry if I wasn't clear (which reading over it, I don't think I was)... I was referring to config files (and database files) for particular programs.  All so that I could be lazy and just drop them in on a fresh install of xubuntu/ubuntu.

I didn't want to save any config files that are related directly to ubuntu or xwindows as they are not working!

Thanks for the reply!

---

### Post by searchfgold6789 on 2011-04-07
Well, it's good that you're getting to a desktop now.
If purging and reinstalling xorg doesn't work try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
EDIT: Actually, before you do that, I would install the video drivers and then patch them - I remember having similar issues with nVidia and then they were fixed when I installed drivers.
Also, avoid the drivers from the website. Always see Applications > System > Hardware Drivers first. Just making sure ;)

---

### Post by djetch on 2011-04-07
Thanks for the suggestion.

Something interesting: If I click on the "show desktop" button on the bottom panel I get an error stating that either my desktop environment doesn't support it or I'm not running a desktop environment.

That's got me wondering if Xfce installed correctly?!  This is the rabbit hole that I'm going down now.

---

### Post by djetch on 2011-04-07
Open the bubbly and light the fireworks.  Apparently the ID10T cable was bad.  Hehehe.

Granted my GNOME environment still has something wrong with it, I was failing to select Xfce or Xubuntu as my session when logging in.  Now everything is working just fine from what I can tell.  Double checking everything now.

Thanks again for the suggestion!  I'm sure you'll be seeing more from me.  I tend to attract the crazy issues that are most of the time, caused by me!

---

