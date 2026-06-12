---
title: "Problem with Desktop effects despite drivers being installed, 9.10"
date: 2010-05-10
forum: General Help
---

### Post by Ulysses on 2010-05-10
Hello,

AMD64 processor with 2GB RAM
PCI Express GeForce 7300 SE/7200 GS
The driver is installed as a NCIDIA restricted driver.

I did the upgrade to 10.04, it didn't work all that well, so I bought a new HDD and now I have two.
HDD1 = 500GB, Ubuntu 10.04
HDD2 = 1TB, Ubuntu 9.10

I have a problem with the displays in both. But I'll beg for help with 9.10 in this thread (my wife likes it better) and then beg for help with 10.04 once this is solved.

Twinview works. One wallpaper spread across both screens. I like.
Compiz does not. 
Go into System>Preferences>Appearance Preferences and try to enable Visual Effects and the only error message I get is "Desktop Effects could not be enabled"

Before my install? Worked just fine. Now? Not so much. No desktop cube, no effects. Nothing.

I've been installing and uninstalling and trying silly things like that and getting nowhere. Once someone points me in the right direction with this, maybe I can get on to finding out why my 10.04 install won't enable Twinview but the desktop effects work.

Thanks, all.

RAR

---

### Post by lavinog on 2010-05-10
Have you tried system>administration>hardware drivers
You need the proprietary nvidia driver for desktop effects to work.

---

### Post by Ulysses on 2010-05-10
Hello,

Just realized there was a typo in my post. Did not preview it well enough.
NVIDIA driver not NCIDIA.

At any rate, yes, Version 185 is active.
And a screen shot of my whole display is attached to this post.

I'm at a loss and I'm likely missing something simple.

RAR

---

### Post by Ulysses on 2010-05-10
Hello,

Okay.

Went here [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check) to see if I had the right setup.
I get the following output
```

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

ulysses@dublin:~$ 
```

I have the ability but not the capacity. I am so confused. All it tells me is that they cannot be enabled.

Anyone else have any ideas? It used to work. I swear it did.

RAR

---

### Post by Ulysses on 2010-05-10
Hello,

Went and installed apt:simple-ccsm?section=universe to find that it wasn't installed either.
This time, when I went to change the appearance, I received more options but the same thing was in error.

Wow but if this isn't frustrating. But I'm learning.

RAR

---

### Post by Ulysses on 2010-05-10
Hello,

I think I solved my own problem.
I followed the steps above and then used my friend Google to figure things out.
This is where I got to.

[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

So far, it looks kinda stable but Lord knows.
I'll keep this posted, for what it's worth.

Anyone else that wants to speak up and warn me of what I might blow up, please do so. I can't afford another machine right now.

RAR

---

