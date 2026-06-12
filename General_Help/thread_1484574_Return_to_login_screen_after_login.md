---
title: "Return to login screen after login"
date: 2010-05-15
forum: General Help
---

### Post by ajmurmann on 2010-05-15
Hi everyone,

I installed a bunch of updates this morning and am encountering the following problem since I restarted after that:
After I login, the screen will flicker once and then return to the login screen. I assumed that something must be wrong with my graphic settings (as so often). So I logged in via Ctrl+Alt+F3 and checked the xorg.conf and Xorg.0.log for erros. Everything seemed all fine. I also ran ```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
``` as recommended in [this thread]("http://ubuntuforums.org/showthread.php?t=1384283"). Also no success. I ran "sudo service gdm restart". That showed me at first a dialog box saying that my graphics card and input device settings could not be detected. I then chose to have a new configuration for this hardware created. This only resulted in the screen flickering for longer when I logged in again and then returning to the login screen.

Any suggestions what else I shoudl try?

---

### Post by fiftyeight on 2010-05-16
I also have this problem after a number of automatic updates were applied last night. 

I thought it might be related to a user profile issue and so created a new user to try that out. I get exactly the same problem.

I've also tried the actions noted above and in the linked thread.

I'm running Lucid on an Asus eeePC 1000H.

Does anyone have any ideas before I try a fresh install?

---

### Post by askPrins on 2010-05-16
Ubuntu 10 : After a successful login it returns directly back to login screen again. 
I install some updates yesterday before I shut down the computer(stupid stupid me) .
Do I have to reinstall the whole damn Ubuntu again?
Why Can't a software be tested before it pushes it to the users? 
Not even Bil Gates would do that :)

---

### Post by Copernicus1234 on 2010-05-16
Do you guys have nvidia cards?

If so, try to run the command "nvidia-xconfig" and see what happens. It will make a backup of your old xorg-config so there is no harm trying it and seeing what it says. It will attempt to generate a xorg config file for you.

It may also help to try and reinstall the nvidia drivers first. Im not sure how to do that from a terminal, maybe "sudo apt-get install nvidia" will work or something along those lines.

---

### Post by fiftyeight on 2010-05-16
No, I don't have an NVIDIA card. The eeePC has an integrated Intel 945GME Express graphics controller.

Is there any way to identify what has been "upgraded" and roll it back to the previous version?

Automated updates are great when they "just work" but if there is no trust the it is likely that we will need to go through full testing regimes before deployment to live. 

Fortunately my device is just for personal use and it is not my primary computer. If this was my workplace then we would probably **not** run automated updates because we can't be sure of the impact.

---

### Post by askPrins on 2010-05-16
I don't have nvidia either. My display adapter is ASUS EAH4350 series.

---

### Post by ajmurmann on 2010-05-16
Thanks for all the hints. I actually have an nvidia card.
I yesterday ran nvidia-xconfig and also downloaded the latest version of the nvidia driver and it didn't help. 

However, I found the following error in my syslog:
> localhost gdm-simple-greeter[1144]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
localhost gdm-session-worker[1159]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

There is a bug report related to that error: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/539440?comments=all]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/539440?comments=all")

So I assumed the problem was gdm related and tried to rollback recent updates to gdm, which I failed to do. So I install kde in addition. That worked which confirms my believe that the behavior comes form gdm and can not be blamed on the graphics card. This way I am at least capable of getting some work done.

Do you other guys see the same error in /var/log/syslog ?

I am very disappointed that I have to fear every time I run automatic updates. In the past it always was my graphics card driver that got busted (Compiz still doesn't work fully on my laptop...) and now this. Things like this seriously make me think about switching to Apple, which I dislike as a company and keep me from putting Ubuntu on my parent's computer.

---

