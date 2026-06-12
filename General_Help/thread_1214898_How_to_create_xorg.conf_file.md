---
title: "How to create xorg.conf file?"
date: 2009-07-16
forum: General Help
---

### Post by Vorsplummi on 2009-07-16
Hi!

I'm a pretty new with Ubuntu and I'd like to ask how to create xorg.conf file.
Resolution in Gnome is 1280x800 but in Gdm it's way too big (about 1920x1440)

I've been told it's becouse X doesn't recognize the screen.

This is my xorg.conf:

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Thanks for help and sorry for my bad english

---

### Post by roccivic on 2009-07-16
Try: 

```
sudo dpkg-reconfigure x.org-server
```

---

### Post by doas777 on 2009-07-16
> **roccivic said:**
> Try: 

```
sudo dpkg-reconfigure x.org-server
```

or better, try
```
sudo dpkg-reconfigure -p high xserver-xorg
```

but that will reset your xorg to default, which looks a lot like what you already have.

---

### Post by vinutux on 2009-07-16
check here..**[COLOR="Red"]System>preferences>display[/COLOR]**

---

### Post by Vorsplummi on 2009-07-16
Yes I have tried all those things but it doesnt work. Like I said resolution is right in gnome but wrong in gdm. 

I was wondering can I add the right resolutions in the xorg.conf file...

---

### Post by Vorsplummi on 2009-07-27
Problem solved.
Only thing I had to do was create a new subsection in xorg.conf.

---

