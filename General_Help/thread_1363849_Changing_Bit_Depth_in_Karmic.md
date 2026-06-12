---
title: "Changing Bit Depth in Karmic"
date: 2009-12-25
forum: General Help
---

### Post by eeshking on 2009-12-25
Hello all,

I am trying to change the default bit depth of X to 16, as I've heard it can help with some games in Wine. I've already noticed that Ubuntu 9.10 (Karmic) does not come with an xorg.conf file by default, so I took the liberty of creating one myself by using

```

sudo service gdm stop
sudo Xorg -configure
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start

```

Now, I've read elsewhere that the xorg.conf file should have a "DefaultDepth" field in the "Screen" section but my xorg.conf file has no such field in the "Screen" section. Rather, it has several "Display" subsections within the "Screen" section that look like the following:

```

SubSection "Display"
		Viewport   0 0
		Depth     1

```

There are 5 such subsections; each one is identical except for the Depth value (one has "Depth 1", one has "Depth 4", one has "Depth 8", etc.)

So, to return to my original question: how can I configure X to have a default bit depth of 16, given that there is no "DefaultDepth" value in xorg.conf?

Any help is greatly appreciated.

eeshking

---

### Post by gsmanners on 2009-12-25
If it helps, here's my xorg.conf:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

---

### Post by eeshking on 2009-12-25
Hm, interesting. I'm on an Asus EEE PC 1005HA (running UNR 9.10) so I have Intel graphics (not nVidia). I guess that means that this problem is specific to my hardware, after all. Still, I'd like to figure out why xorg.conf is so different and how to change bit depth if at all.

---

### Post by eeshking on 2009-12-25
Solved!

I just had to add the line 

```

DefaultDepth 16

```

which did not previously exist after the

```
Section "Monitor"
```

line in xorg.conf. Then, I restarted X and checked the bit depth of various windows using

```
xwininfo
```

and voila! It had been changed to 16 bit. Thanks for your help!

---

### Post by dragon_788 on 2010-01-22
Thanks fellas, actually used this to change the bitdepth default to 24 since apparently in VMware its 16. Now I can play with XBMC in VMware ESXi, though now that begs the question of..................why?

---

