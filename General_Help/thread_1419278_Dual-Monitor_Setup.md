---
title: "Dual-Monitor Setup"
date: 2010-03-01
forum: General Help
---

### Post by amtur_poet on 2010-03-01
I'm having trouble setting up dual monitors on my HP Pavilion dv7-1020us laptop, with an Nvidia 9600M GT graphics card, and Ubuntu 9.10. I installed Ubuntu via Wubi, on top of Windows 7. I tried this before on the same laptop when I was using Vista and Wubi, and Ubuntu was able to recognize my Graphics card, and install a proprietary driver. I wasn't able to test dual monitors, though. However, now that I'm using W7 and Ubuntu, it cannot use a dual-monitors correctly. It recognizes the monitor, but it only displays a mirror display of my Laptop monitor, not acting as a separate monitor, like I want it to. I tried messing around with the settings in the display menu, but nothing works. I tried downloading linux drivers for my card from Nvidia's site, but the file is in a .run extension, which I don't know how to install. What should I do to get this working?

---

### Post by bodhi.zazen on 2010-03-01
Install the nvidia drivers from the Ubuntu repositories. It should be an option in restricted drivers.

then configure your monitiors with:

```
gksu nvidia-settings
```

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by amtur_poet on 2010-03-01
Thank you, it worked, but now I have another problem. When I try to enable Extra visual effects [Compiz], it searches for available drivers,and then gives me an error message saying "The composite extension is not available". What should I do to enable compiz?

---

### Post by drewsus on 2010-03-01
try **_[Compiz Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")_** to see if you can get any hints. Its helped me in the past.

---

### Post by Fenris_rising on 2010-03-01
i had an issue initially getting dual screens and compiz working. What seemed to help was to set the screens to mirror in the display gui then compiz would initiate. reset screens to not mirror and it all worked. i havent had to do anything since. YMMV

regards

Fenris

---

### Post by amtur_poet on 2010-03-02
> **drewsus said:**
> try **_[Compiz Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")_** to see if you can get any hints. Its helped me in the past.
I ran the script, and got this output:
```
chris@ubuntu:~/Desktop$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...Xlib:  extension "RANDR" missing on display ":0.0".
           [ OK ]


```

---

### Post by drewsus on 2010-03-10
It didnt output anything else about the fail?

---

### Post by drewsus on 2010-03-10
also, Im curious, did you upgrade from 9.04 or do a fresh install of 9.10?
That is, do or do you not have an xorg.conf? What is the output of: 
```
cat /etc/X11/xorg.conf
```

---

