---
title: "Resolution Problem.."
date: 2010-10-28
forum: General Help
---

### Post by DirtyPC on 2010-10-28
Hello. I now have ubuntu 10.10 64bit with an intergrated hd4200 driver, the drivers install fine, but when i go to monitors> resolution the only option i have is 1024x768, i need 1280x1024!!

any ideas? :/

---

### Post by linux-hack on 2010-10-28
try a ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DirtyPC on 2010-10-28
> **linux-hack said:**
> try a ```
sudo dpkg-reconfigure xserver-xorg
```
done that, now when i restart i get the same problem at login when i had 10.04 32 bit, i hate having to press ctrl+alt+-!!!!

---

### Post by Grenage on 2010-10-28
Are you open to a custom xorg.conf file?  It's generally a more sure-fire solution.

---

### Post by DirtyPC on 2010-10-28
i dont really know, but its worth a try

---

### Post by Grenage on 2010-10-28
I have a guide [here]("http://www.grenage.com/xorg.html"); if you get stuck, post your monitor make and model, and I'll knock one up for you.

As usual, if you can manage it yourself - that's the best way.

---

### Post by DirtyPC on 2010-10-28
Completely off topic, I see you're from Pompey! I was born/lived there til last year!

---

### Post by DirtyPC on 2010-10-28
I am completely lost, heres my monitor 
**[Sony SDM-E96D]("http://www.techeblog.com/index.php/tech-gadget/sony-sdm-e96d-reviewed")**

---

### Post by Scunnered on 2010-10-28
I to have a resolution problem relating to 10.10.  Unlike harrylucas1e I whilst seeing that the 1024 x 768 option is available to me it will not properly display on my laptop.  If I attach the laptop to a separate screen there are no problems.  This suits quite well when I am working at home but when taking the laptop away from my home it is a complete pain in the neck.

I using 10.04 have no problem with the display as it will fully populate the screen but 10.10 does not.  I have attached a photo which I hope will be of assistance.

I hope that you can offer assistance as frustration is setting in.

---

### Post by Grenage on 2010-10-28
> **harrylucas1 said:**
> Hello. I now have ubuntu 10.10 64bit with an intergrated hd4200 driver, the drivers install fine, but when i go to monitors> resolution the only option i have is 1024x768, i need 1280x1024!!

any ideas? :/

Let's try this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Sony"
	ModelName "SDM-E96D"
	HorizSync 28 - 80
	VertRefresh 56 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "ati"
	VendorName "ATI hd4200"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

If that doesn't work, add the following below VertRefresh:

```
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```


> **harrylucas1 said:**
> Completely off topic, I see you're from Pompey! I was born/lived there til last year!

Well done on escaping! :)

---

### Post by Grenage on 2010-10-28
> **Scunnered said:**
> I to have a resolution problem relating to 10.10.  Unlike harrylucas1e I whilst seeing that the 1024 x 768 option is available to me it will not properly display on my laptop.  If I attach the laptop to a separate screen there are no problems.  This suits quite well when I am working at home but when taking the laptop away from my home it is a complete pain in the neck.

I using 10.04 have no problem with the display as it will fully populate the screen but 10.10 does not.  I have attached a photo which I hope will be of assistance.

I hope that you can offer assistance as frustration is setting in.

I'm wondering if that's an xrandr issue, and that it could be used to correct the desktop sized (I have little experience there).  It might be worth creating a separate thread for that; while we could use an xorg.conf, it probably wouldn't toggle well between two displays.

---

### Post by DirtyPC on 2010-10-28
> **Grenage said:**
> Let's try this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Sony"
	ModelName "SDM-E96D"
	HorizSync 28 - 80
	VertRefresh 56 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "ati"
	VendorName "ATI hd4200"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

If that doesn't work, add the following below VertRefresh:

```
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```




Well done on escaping! :)
hehe ;)

So where do i put these codes.. in the terminal? or xorg.conf? if so how and where? :-)

---

### Post by Grenage on 2010-10-28
> **harrylucas1 said:**
> hehe ;)

So where do i put these codes.. in the terminal? or xorg.conf? if so how and where? :-)

Silly me, lol.  Save a copy of your existing xorg.conf (if you have one):

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.oldconf
```

Now open a new one:

```
gksu gedit /etc/X11/xorg.conf
```

Save it, and restart Gnome (or just reboot the PC).  It's very unlikely, but if you have problems when you reboot, you can delete the new one and rename the old one.

---

### Post by DirtyPC on 2010-10-28
> **Grenage said:**
> Silly me, lol.  Save a copy of your existing xorg.conf (if you have one):

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.oldconf
```

Now open a new one:

```
gksu gedit /etc/X11/xorg.conf
```

Save it, and restart Gnome (or just reboot the PC).  It's very unlikely, but if you have problems when you reboot, you can delete the new one and rename the old one.
I will try this now! Thank-you my Pomparian friend, you have been very helpful and you make this forum a pleasure to visit :-)

---

### Post by DirtyPC on 2010-10-28
> **Grenage said:**
> Silly me, lol.  Save a copy of your existing xorg.conf (if you have one):

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.oldconf
```

Now open a new one:

```
gksu gedit /etc/X11/xorg.conf
```

Save it, and restart Gnome (or just reboot the PC).  It's very unlikely, but if you have problems when you reboot, you can delete the new one and rename the old one.
Welll its the right resolution, but all my visual effects have dissapeared, and it cant find my drivers :(

---

### Post by DirtyPC on 2010-10-28
> **harrylucas1 said:**
> Welll its the right resolution, but all my visual effects have dissapeared, and it cant find my drivers :(
and i dont know if you need this.. (its my old xorg.conf file, the first one..

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

---

### Post by Grenage on 2010-10-28
Ah of course, proprietary driver!

Replace the driver *ati* on the config I gave you, with *fglrx*.

---

### Post by DirtyPC on 2010-10-28
> **Grenage said:**
> Ah of course, proprietary driver!

Replace the driver *ati* on the config I gave you, with *fglrx*.
That made sense to me! ahah finally Terminal codes and .conf files make sense! I'm learning, is it me or is there something really rewarding about typing codes into the terminal.. :P I will try this now thankyou..

---

### Post by DirtyPC on 2010-10-28
> **Grenage said:**
> Ah of course, proprietary driver!

Replace the driver *ati* on the config I gave you, with *fglrx*.
You sir, are a genius, it worked! Thankyou so much, you've been very helpful :-). Off topic, where did you learn about all the terminal codes? And where could I learn these as i'm very interested :-)

---

### Post by Grenage on 2010-10-28
Wonderful! Very glad to hear it. :)

I was once stuck as you were, and was basically forced to hash out configs.  These days all you really ever need to specify is the basic options, the rest is done automatically.

---

### Post by DirtyPC on 2010-10-28
> **Grenage said:**
> Wonderful! Very glad to hear it. :)

I was once stuck as you were, and was basically forced to hash out configs.  These days all you really ever need to specify is the basic options, the rest is done automatically.
Brilliant, thanks! :-)

---

