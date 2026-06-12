---
title: "nvidia-settings antialiasing"
date: 2011-09-21
forum: General Help
---

### Post by ahso4271 on 2011-09-21
Hi
nvidia-settings has no effect? how to set antialiasing?
Thanks

---

### Post by searchfgold6789 on 2011-09-21
I don't remember where the setting is, but it's not in the Nvidia thing, it's in some other graphics options.

---

### Post by ahso4271 on 2011-09-22
sigh...

---

### Post by papibe on 2011-09-22
I believe you have to run nvidia-settings as root:
```
$ gksudo nvidia-settings
```
Set your antialiasing settings, and then use the option 'Save to X Configuration file', the save those options to both the global /etc/X11/xorg.conf, and the personal  ~/.nvidia-settings-rc

Be sure that you have an entry in your 'Startup Applications' that loads your settings when you login. It should be something like this:
```
nvidia-settings --load-config-only
```
I hope it helps,
Regards.

---

### Post by ahso4271 on 2011-09-22
ok all works. seems that flightgear needs special treatment.

---

### Post by papibe on 2011-09-22
:p Glad to know. Mark the thread solved when you have the chance.

Regards.

---

### Post by lookabout on 2013-01-23
> the save those options to ...   /etc/X11/xorg.conf

??? :confused:

that is, if you want to scrap your X config and get a "no screens found" error when starting X?

I'm such a noob I blindly followed these instructions, but future readers don't have to :D  just saving to the ~/.nvidia-settings-rc and adding a startup command works fine.

---

