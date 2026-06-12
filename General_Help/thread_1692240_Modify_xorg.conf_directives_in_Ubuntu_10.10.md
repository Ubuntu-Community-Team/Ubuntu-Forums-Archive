---
title: "Modify xorg.conf directives in Ubuntu 10.10"
date: 2011-02-21
forum: General Help
---

### Post by dualityim on 2011-02-21
I'm trying to improve the functionality of my mouse in my installation of Ubuntu 10.10 desktp 64-bit running inside a VMware workstation VM running on a Windows 7 64-bit host. I stumbled upon some instructions suggesting changing a xorg.conf directive (specifically, change the mouse protocol from "imps/2" to "explorerps/2") which I'd like to try out. However there is no xorg.conf file in Ubuntu 10.10. I tried using Xorg -configure to generate the file and placing it in /etc/X11/xorg.conf, but it seems to make no effect. Using "xinput list" the mouse is still listed as imps/2 even after I changed the xorg.conf file and rebooted. It seems Ubuntu 10.10 ignores the xorg.conf file completely? If that's the case, is it possible to manually specify this setting that used to belong to xorg.conf at all? Thanks.

---

### Post by whatthefunk on 2011-02-21
I dont think there is an xorg.conf file by default.  You have to make one.  The full path would be /etc/X11/xorg.conf 

```
sudo nano /etc/X11/xorg.conf
```

This will open up the file for you.  Do some research on the format the file needs to take before messing around with it.

---

### Post by dualityim on 2011-02-21
> **whatthefunk said:**
> I dont think there is an xorg.conf file by default.  You have to make one.  The full path would be /etc/X11/xorg.conf 

```
sudo nano /etc/X11/xorg.conf
```

This will open up the file for you.  Do some research on the format the file needs to take before messing around with it.

I tried creating one but the changes I put into it seem to have no effect. Is there some kind of debug directive I can put into xorg.conf that lets me see if the file is being used at all? I tried deleting the mouse section completely but I still have a working mouse, which leads me to believe that the system is completely ignoring the /etc/X11/xorg.conf file I put in.

---

