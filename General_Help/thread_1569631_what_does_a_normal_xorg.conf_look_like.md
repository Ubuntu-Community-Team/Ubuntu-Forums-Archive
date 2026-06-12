---
title: "what does a normal xorg.conf look like?"
date: 2010-09-07
forum: General Help
---

### Post by Vigh on 2010-09-07
hi I was just wondering what a normal xorg configuration file looks like, I want to add some lines in so that it looks for the intel mesa drivers first but when ever I open it up to edit it, it comes up blank (the xorg.conf file that is), ive been using sudo gedit to try and open the conf file, cheers

---

### Post by squaregoldfish on 2010-09-07
Does the file actually exist? These days xorg.conf is not generally used, as Xorg is pretty good at figuring out settings for itself.

If you want a starting point for a custom xorg.conf file, you can get Xorg to dump its detected settings:
[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

Steve.

---

### Post by Vigh on 2010-09-07
Cheers, I want to create a custom xorg-xserver config to try out the open-source 3D intel mesa drivers.

---

### Post by wojox on 2010-09-07
Have you tried 

```
sudo Xorg -configure 
```

---

### Post by asmoore82 on 2010-09-07
For modern distros, xorg.conf is not necessary.

The super-duper awesome thing is that you can make the file as minimal as possible and
it will still honor your choices while automagically configuring the rest.

So, for my Laptop with intel graphics, I have no xorg.conf at all.
My wife's laptop with nVidia graphics, needs just enough to load nVidia's driver:
```

**$ cat /etc/X11/xorg.conf**

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by Vigh on 2010-09-08
So I don't need the default modules loading in the xorg.conf file??? I have done some experimentation getting 3D intel graphics and broken the xorg a few times. Thought that it might be because I need all the normal xorg settings in the customized xorg.conf file.

---

### Post by jocko on 2010-09-08
> **Vigh said:**
> ... Thought that it might be because I need all the normal xorg settings in the customized xorg.conf file.
Everything is detected automatically by xorg, so whatever you leave out of your customized xorg.conf will simply continue working exactly as it does without any xorg.conf.
To load another driver than the default, all you need is this (provided the driver is properly installed):
```
Section "Device"
    Identifier    "Default Device"
    Driver    "[COLOR=Red]drivername[/COLOR]"
EndSection
```

---

