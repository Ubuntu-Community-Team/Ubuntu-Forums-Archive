---
title: "My screen is off center!"
date: 2006-04-15
forum: General Help
---

### Post by Russty of Oz on 2006-04-15
Hello, :) 

I have only just finished installing Breezy Badger and so far I think it is great.  

The problem I have is that my screen is a bit too far to the right, so I have a black vertical bar on the left and the close button on pages is not visible on the right.  

Does anyone know how I can adjust it?  I have tried different screen resolutions but with no success.  ](*,) 

Russty.

---

### Post by Perfect Storm on 2006-04-15
First find your Monitor manual (or google it).
Then find where it mention something about **HorizSync** and **VertRefresh**.

Next open the terminal:
```
sudo gedit /etc/X11/xorg.conf
```

Go to the **Section "Monitor"**
and add the correct **HorizSync** and **HorizSync**

CAUTION: Make sure it's correct it can damage your monitor if you use incorrect numbers!
save and exit. Reboot.

Eg. Mine looks like this:
```
Section "Monitor"
    Identifier     "DELL P992"
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS"
EndSection

```

---

### Post by r4ik on 2006-04-15
Adjust it on your monitor they are not all quitte the same but there must be a button there.
Use adjust horizontal if you can find it.
Perhaps there is a manual ?

Good luck !

---

### Post by dermotti on 2006-04-15
Another way

backup your /etc/X11/xorg.conf


and run **sudo dpkg-reconfigure xserver-xorg**

---

### Post by Russty of Oz on 2006-04-15
Thanks Guys!! :-D 

I looked at the Section "Monitor"  bit but there was no mention of any HorizSync, then I saw the second reply from r4ik and pressed some buttons on the screen, and PRESTO! it was fixed!!!  

That is problem No. 1 fixed.  :)

---

### Post by Perfect Storm on 2006-04-15
You can add it HorizSync etc. to you monitor section. It will also make sure that the resolution and refresh rate is correct (optimized).

---

### Post by gibson on 2006-04-15
I had the same problem.

Was sorted out when i installed the nvidia drivers rather than using the ones that come on the default ubuntu install.

There is a good howto in the tips&tricks section

hth

---

### Post by subtler on 2006-04-22
same problem here. I installed the nvidia drivers from automatix and the problem cleared up for me.

---

### Post by jongkind on 2006-04-23
There is a special tool for this, an explanation can be found after following the ling below (section "How to adjust position of your screen").

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Herman

---

### Post by sinkxdie on 2006-04-23
Haha, that always happens with a fresh install for me. But I have a button on my monitor.:D

---

