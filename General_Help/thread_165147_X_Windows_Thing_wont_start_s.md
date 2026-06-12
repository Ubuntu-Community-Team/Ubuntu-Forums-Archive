---
title: "X Windows Thing wont start :s"
date: 2006-04-24
forum: General Help
---

### Post by supremejosh on 2006-04-24
Hi, sorry I am noob to linux but I have managed to break something lol. I was trying to get xgl working on ubuntu 6 dapper and some guide thing told me to do this:

sudo ln -sf /usr/bin/Xgl /etc/X11/X

So I did, however then when I restarted the computer afterwards it didnt work. The login screen didn't load, all I got was the colored background and the egg-timer cursor thing doing nothing.

Then in the alt+ctrl+f1 terminal my friend told me to enter 

sudo ln -sf /usr/bin/X /etc/X11/X

So I did that, although then instead of jamming and not loading the log in screen it didn't load anything whatsoever, and gave me some terrible error message in a window sort of thing made out of ascii characters. I selected the option to see the x output to diagnose the problem but it just gave me a blank box.

I also did sudo ln -s /usr/X11R6/bin /usr/bin/X11 cause it told me too on some website. I am still not any better off :S

So, if anyone knows what I have managed to do and any way to reverse/fix it I will be very happy!

---

### Post by John64 on 2006-04-24
Which video card are you using?

If you dont know, type CTRL+ALT+F1 to get to the first text mode console.  From there type "sudo nano /etc/X11/xorg.conf" and look for the graphics card section.  Change driver from whatever is there (nv, nvidia, fglrx, ati, radeon are common ones) to vesa.
Here is mine for a Radeon card using ati's binary driver:
```

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "fglrx"
        BusID       "PCI:3:0:0"
EndSection

```
to
```

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:3:0:0"
EndSection

```

Those drivers i mentioned:
nv - open source Nvidia Driver
nvidia - binary only driver
ati - generic ATI driver open source
radeon - generic ATI Radeon driver open source
fglrx - ATI binary only driver

I dont know of other manufactures drivers

---

### Post by supremejosh on 2006-04-24
Wow! That worked??!? So now that I can get to my desktop do I need to do something to fix what I broke so I can revert to my fglrx drivers?

Thanks BTW

Edit: I have a radeon 9600pro running fglrx if that makes any difference

Edit 2: Where abouts should the file /etc/X11/X point to? Is it even supposed to exist? Cause I think I linked it to something at some stage...

---

### Post by supremejosh on 2006-04-24
EDIT: THANKS! I booted up in that vesa mode thing and then rebooted with my fglrx things and now it all works fine! Thanks a tonne :)

---

