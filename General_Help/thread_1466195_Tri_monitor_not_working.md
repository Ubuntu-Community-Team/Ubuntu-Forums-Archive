---
title: "Tri monitor not working"
date: 2010-04-30
forum: General Help
---

### Post by JigglyWiggly_ on 2010-04-30
Ok so I have a hd3870x2, this is not a standard video card. It is the ONLY ati video card, ati does not support in their drivers... assholes.

Anyway, but default Ubuntu has some drivers, compiz works and all. So at defualt I had an 8400gs, for my 2nd videocard to drive my 2nd and third monitors. Nothing was coming up, so I tried installing the nvidia drivers from restricted panel, bad idea, system wouldn't boot...

I unplugged it, installed my old hd3870 for my 2nd videocard(not x2!), replacing the 8400gs.

It offered if I want to go in low graphics, yeaeh yeah, delete old xorg file, it generates a new one... so far so good.

Reboot, I got compiz working again etc, but I still can't use my 2nd and thrid monitors!

Any ideas?

---

### Post by dino99 on 2010-04-30
you might need to tweak a custom xorg.conf with screen1, screen2, screen3 and define settings for each ( like to the old jaunty time)

[http://ubuntuforums.org/showthread.php?t=361124](http://ubuntuforums.org/showthread.php?t=361124)

google around the key words: xinerama & twinview

---

### Post by JigglyWiggly_ on 2010-04-30
Any reason I have to do that? I also tried an x1550 pci, same thing. Even tried fgrlx, says Unknown device, on both the x1550, and the 3870.

I have a nvidia system, and it works plug n play :?

---

### Post by JigglyWiggly_ on 2010-04-30
So how would I edit my xorg.conf? I mean Here are the contents of it atm, I am using fgrlx

```

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

```

I have to add another Device, the hd3870, and add the two monitors...

But I have no idea what the BusID for the hd3870 is, or the identifier!

---

### Post by JigglyWiggly_ on 2010-05-01
Well for anyone else, go into the terminal and type
Xorg -configure I think it was. It made my two other monitors work, hurrah! ((to new users): KIll gnome first! /etc/init.d/gdm stop then press ctrl + alt + f2 to switch desktops)

Except they are mirroring eachother, left and right are.

The config file is in your /home/usenrame/ copy and paste that to your /etc/X11/ and replace the old xorg.conf (renaming your new generated conf)

Play around with that file to maybe get it working, I was about too, until my install started getting corrupted files(not related to this), and I just got a headache and went back to Windows on my desktop. Not sure why corrupt files happened, never happened on any other of my pcs. (Network manager dissapeard, etc etc)

After that I got mad and did sudo rm -rfv /*

---

