---
title: "Custom Brightness Settings Return to Default in NVIDIA X Server Settings Upon Reboot"
date: 2009-12-19
forum: General Help
---

### Post by martini1179 on 2009-12-19
I've just upgraded to Karmic, and like the title says, I'd like to change my brightness in the NVIDIA X Server Settings (like I was able to to effortlessly in Jaunty) and have those changes survive a reboot, but they currently don't. I'm running a GTX 260 and I've tried uninstalling/reinstalling the Ubuntu NVIDIA device drivers, but to no avail. Any ideas? 

I'd rather not change the brightness directly on the monitor. Personal preference. 

Let me say that I've looked through several similar threads and none seem to address my specific problem. Usually their solution is to start nvidia-settings as root and change some settings in X Server Display Configuration, and click on the "Save to X Configuration File," except that when I preview the changes to X, there's nothing there about brightness. 

Thanks in advance!

---

### Post by pbrane on 2009-12-19
When you save the current configuration in nvidia-settings it creates the file ~/.nvidia-settings-rc. What I did was to add **nvidia-settings --load-config-only** to my startup applications. I tried using ~/.xinitrc but that doesn't work for me. Have a look at *man nvidia-settings*.

---

### Post by diablo75 on 2009-12-19
In my experience to get settings to stick I have to run nvidia-settings from the terminal with sudo.

```
sudo nvidia-settings
```

Try this; hopefully the settings will hold after you save them.

---

### Post by martini1179 on 2009-12-19
One very important thing I can't believe I forgot to mention is that, the brightness settings are "saved," but aren't APPLIED upon reboot until I run the NVIDIA X Server Settings.

---

### Post by martini1179 on 2009-12-19
> **diablo75 said:**
> In my experience to get settings to stick I have to run nvidia-settings from the terminal with sudo.

```
sudo nvidia-settings
```

Try this; hopefully the settings will hold after you save them.

I tried this, but it didn't work.

---

### Post by Lukas666 on 2009-12-19
> **martini1179 said:**
> One very important thing I can't believe I forgot to mention is that, the brightness settings are "saved," but aren't APPLIED upon reboot until I run the NVIDIA X Server Settings.

by "saved" you mean saved in xorg.conf?

---

### Post by pbrane on 2009-12-19
read *man nvidia-settings*. nvidia-settings does not save anthing but the driver to xorg.conf. All other settings are intentionally not saved unless you save them using the "save current configuration" button. That saves them to ~/.nvidia-settings-rc. In order to restore your saved settings you have to run *nvidia-settings --load-config-only* at login.

---

### Post by martini1179 on 2009-12-19
> **Lukas666 said:**
> by "saved" you mean saved in xorg.conf?

No, I mean saved via the NVIDIA app.

---

### Post by martini1179 on 2009-12-19
> **pbrane said:**
> read *man nvidia-settings*. nvidia-settings does not save anthing but the driver to xorg.conf. All other settings are intentionally not saved unless you save them using the "save current configuration" button. That saves them to ~/.nvidia-settings-rc. In order to restore your saved settings you have to run *nvidia-settings --load-config-only* at login.

So I'm to infer that this is some sort of bug, since I didn't have this problem until I upgraded to Karmic? 

Also, do you mean I should run "nvidia-settings --load-config-only" in, say, Startup Applications?

---

### Post by pbrane on 2009-12-19
> 
So I'm to infer that this is some sort of bug, since I didn't have this problem until I upgraded to Karmic? 

According to the man page it's not a bug. I have never been able to get certain settings to reload automagically. It's supposed to be so that settings can be set on a per user basis. If you look at the man page under USER GUIDE: Loading Settings Automatically it explains how this works. Here is an excerpt.

> 
3. Loading Settings Automatically
       The NVIDIA X driver does not preserve values set  with  nvidia-settings
       between  runs  of  the X server (or even between logging in and logging
       out of X, with xdm(1), gdm, or kdm ).   This  is  intentional,  because
       different users may have different preferences, thus these settings are
       stored on a per-user basis in a configuration file stored in the user's
       home directory.


> Also, do you mean I should run "nvidia-settings --load-config-only" in, say, Startup Applications?

Yes, that's what I have to do. I haven't had any success getting nvidia-settings to work in ~./xinitrc or ~/.xsession.

---

### Post by Linuxforall on 2009-12-19
gksudo nvidia-settings and your settings will stick in next reboot.

---

### Post by martini1179 on 2009-12-19
> **pbrane said:**
> According to the man page it's not a bug. I have never been able to get certain settings to reload automagically. It's supposed to be so that settings can be set on a per user basis. If you look at the man page under USER GUIDE: Loading Settings Automatically it explains how this works. Here is an excerpt.

Yes, that's what I have to do. I haven't had any success getting nvidia-settings to work in ~./xinitrc or ~/.xsession.

Thanks, I read the man page, and I'm glad that it worked without creating any other files like xintrc or the like. If it looks like a bug....

Thanks for the help, although it's disheartening to know that this is one of those things that the average Ubuntu user (assuming Linux became more mainstream) would probably give up on and complain about.

---

