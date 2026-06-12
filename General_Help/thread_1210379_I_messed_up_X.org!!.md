---
title: "I messed up X.org!!"
date: 2009-07-11
forum: General Help
---

### Post by Hyper Tails on 2009-07-11
Hi I have Jaunty jakealope and I was trying to change my resolution to 1400X900 (I thought it was 1600X1200 for my monitior but in the manual it was 1400X900) it was on 1400X1050 and I was trying some commands (I forget which ones) and I eventually got it to 1400X900 and I logged out and My screen started messing up and Now I tried recovery mode and that didn't work ethier and I want to use my ubuntu but I can't at the time.

Help will be thanked.
(the reason why I was using a command to change the resolution because twhen I opened display properties the pc would slow down FOR NO REASON!!! and I was unuseable at that speed and Frustrated me)

---

### Post by nice_like_rice on 2009-07-11
Try booting, pressing control+alt+FX, and from command line 
```
sudo dpkg-reconfigure xserver-xorg
```

?

---

### Post by Hyper Tails on 2009-07-11
I tried it and it didn,t work.
I still get that screen

---

### Post by b@sh_n3rd on 2009-07-11
What happens if you *BOOT* to safe mode and try that command? Also, what's your video card? There's no reason your PC should slow down as you put it...Oh and in safe mode you login to root so "sudo" is not necessary and will not be recognised...

---

### Post by Hyper Tails on 2009-07-11
I go into normal boot and do it from there,
when the blank screen comes it doesen't take me to a command propments

---

### Post by wojox on 2009-07-11
You could always copy one of your back up files into xorg.conf
Try xorg.conf.failsafe.

---

### Post by vinutux on 2009-07-11
System-->prefrences-->display

---

### Post by Hyper Tails on 2009-07-11
question:
is it possible to recover x.org with the live cd?

---

### Post by Irihapeti on 2009-07-11
Yes, it is possible to recover xorg with a liveCD. You need to copy the xorg.conf file from the liveCD's /etc/X11 folder to /etc/X11 on your hard drive.

Another thing I learned the hard way is that you also need to remove  xorg.conf.failsafe. Otherwise Ubuntu will use that one instead of your nice new version. I prefer to remove all backup versions of xorg.conf (and there might be a few if you've been fiddling a bit). If you think you might need the settings in them again, copy the files to somewhere else - your home directory, for example - before you delete them.

I did all this in Hardy, after my son had borked his display (the joys of telephone support!). Later Ubuntu versions may have a different way of doing things.

---

### Post by Hyper Tails on 2009-07-12
I tried this and For some reason In hardy live cd it says format type not supported (ex4) and on my jaunty live cd it says that I don't have permission to do it

What do i do?

---

### Post by vinutux on 2009-07-12
open with sudo

```
sudo nautilus 
```

or

Alt+F2  and type ```
gksu nautilus
```

then go and open file from this window

---

### Post by Hyper Tails on 2009-07-12
Hi i reinstalled ubuntu Because nothing Worked and I changed my resolution to 1400X900 and every time I logout it keeps going back to 1400X1050 again

can you help me to keep it at 1400X900

---

### Post by Irihapeti on 2009-07-12
Somewhere in my rather rusty memory something tells me that Jaunty has a different way of managing X settings. I'm at work at the moment, but when I get home I may be able to boot off a Jaunty liveCD (live SD card, actually) and do some research.

---

### Post by vinutux on 2009-07-13
Alt+f2 and type

```
gksu gedit /etc/X11/xorg.conf
```

and changed your resolution there............**[COLOR="Red"]Save[/COLOR]** it 

now check it

..................................

---

