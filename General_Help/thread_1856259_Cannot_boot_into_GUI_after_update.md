---
title: "Cannot boot into GUI after update"
date: 2011-10-07
forum: General Help
---

### Post by QuickSphinx on 2011-10-07
Hi Everyone,

When I boot up Ubuntu. Nothing comes up on the monitor.  Ican boot into console by pressing escape twice(I think its escape twice, to be honest i tap a lot of buttons) - and typing startx but on some times that brings up gui without panels and no internet connection, other times nothing.

Any help is appreciated

---

### Post by [S|G] on 2011-10-08
Hi there! Unfortunately I think you've given us very little information to begin with. Are there any error messages when you type startx? Can you post the contents of your /var/log/Xorg.0.log after you try to start the GUI? You can see that by typing:

$ cat /var/log/Xorg.0.log

You can also try to fix your home directory permissions from the console:

$ sudo chown -R [your username] /home/[your username]

(replace your username as appropriate)

---

### Post by garvinrick4 on 2011-10-08
> Any help is appreciated
What version you running and when you say update did you do a distribution update
from one version to the next version.

---

### Post by QuickSphinx on 2011-10-08
Thanks for the replies,

Im running 11.04, and I think this all came up after a sudo apt-get upgrade.

Is there a way to efficiently copy the 100+ lines of Xorg.0.log in here? After a quick skim through I found a few things:
> 
[132.431] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[132.869] (EE) GLX error: Can not get required symbols.
[133.262] (II) No input driver/identifier specified (ignoring)
Anyways, I type startx and it doesnt bring up anything. I press control alt f2 and it brings me to the console. There, it shows X.Org X Server 1.10.1, release date, protocol version, etc, and at the end of that there is an error message that says GLX error: Can not get required symbols.

Does that tell you guys anything?

EDIT: Startx boots up now. I Can see my wallpaper and desktop icons, but no panels. In the top right corner a grey rectangle shows up  and says in white font "could not apply the stored configuration for monitors" also it says in console: 

(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
it repeats this but the BusID changes to 18:0,18:1,18:2,19:0,19:1,10:2,20:0,20:2,20:3,20:4,20:5

and after that...

Warning: LookupWindow()/SecurityLookupWindow() are deprecated. Please convert your driver/module to use dixLookupWindow()

I feel like im getting closer.

---

### Post by [S|G] on 2011-10-08
You could try what Desktop_n00b did on this post to begin with: [http://ubuntuforums.org/showthread.php?p=11300931](http://ubuntuforums.org/showthread.php?p=11300931)

That way you can eliminate an broken/incomplete upgrade. Basically you'd do this from the terminal (which you can access by pressing ctrl+alt+f1):

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a (only if the system asks due to something being half-installed)


If that doesn't help I'd suggest reinstalling your video card drivers (fglrx is the ATI driver)

---

### Post by QuickSphinx on 2011-10-09
Okay. How can I install the driver? If i put it on a flash drive, how can I access it from the terminal?

EDIT: I installed the driver and it still isn't working. Sigh... I'm just going to settle for a reinstall.

---

