---
title: "Visual Effects Reset at Reboot"
date: 2009-10-28
forum: General Help
---

### Post by CrusaderAD on 2009-10-28
I like my visual effects set at normal or extra. Lately it keeps resetting it to none every time I reboot and I have to set it back to normal. Any ideas on how I can set it to stay that way? I did try emerald for a bit and I think it messed things up.

---

### Post by bgeraghty on 2009-10-28
Which type of X Window System, and what is the name of the Effects Package or Manager that applies the enhancement to it?

---

### Post by CrusaderAD on 2009-10-28
Doesn't Ubuntu just use Compiz?

---

### Post by sancho panza on 2009-10-30
Im having the same problem. Any suggestions?

---

### Post by dmeehan on 2009-11-12
I'm also having this problem. I cant switch it back to Extra either as I just get an error message saying setting desktop effects failed?

I would be greatful for any help on this issue?

It wouldnt bother me so much if I was never able to set the effects to "Extra" but I was able to select this after installing 9.10, but it resets to "None" after I reboot.

---

### Post by CrusaderAD on 2009-11-12
I haven't found an actual solution to this, but a reinstall fixed it for me.

---

### Post by dmeehan on 2009-11-16
> **raptormanad said:**
> I haven't found an actual solution to this, but a reinstall fixed it for me.

i already tried that, Im on my second install as it is

:-(

---

### Post by debsankha on 2009-11-16
> **raptormanad said:**
> I like my visual effects set at normal or extra. Lately it keeps resetting it to none every time I reboot and I have to set it back to normal. Any ideas on how I can set it to stay that way? I did try emerald for a bit and I think it messed things up.

Type ```
compiz --replace
```in a terminal and see if the visual effects return to normal or not. If it does, then just add the command to the startup applications ( Preferences>Startup Allpications)

---

### Post by stinkeye on 2009-11-16
If your using fusion-icon in startup applications try starting it with
```
fusion-icon -n
```
Loads fusion-icon but stops it from trying to load compiz, which is not needed.

---

### Post by vivisectionnnn on 2010-06-24
i am having the same problem with visuals resetting on reboot. but it goes further.
it is very frustrating for me;  every time it resets back to "none" under visuals i end up with no top bar for any window. and it restricts me from minimizing, maximizing, closing, or even moving a window. but as soon as i manually reset my visual setting to custom it works fine.**[SIZE="4"] is this happening to anyone esle ? [/SIZE]**

---

### Post by warfacegod on 2010-06-24
This seems to work for some people. Go to: System> Prefs.> Startup Apps> click Add> name it Compiz> set the Command as: /usr/bin/compiz --replace

Reboot to see if it worked.

---

### Post by PMT24BUZ on 2010-10-22
> **warfacegod said:**
> This seems to work for some people. Go to: System> Prefs.> Startup Apps> click Add> name it Compiz> set the Command as: /usr/bin/compiz --replace

Reboot to see if it worked.

I tried this but compiz crashes with this:
peter@peter-acer:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!

Any suggestions?

---

### Post by warfacegod on 2010-10-22
Unfortunately, I don't. I can't recall what I did last year to fix this. I'm pretty sure I added Compiz to my Startup Apps.

---

### Post by scarybeast on 2011-01-26
I have also had this problem (using Ubuntu 10.10). My Visual Effects setting was always reset to "Normal" after booting.

As it turned out, I had used the "Remember currently running applications" button once, located at System > Preferences > Startup Applications > Options. This does also save the currently running window manager to the saved session.

For me it worked to clean the saved session. For Ubuntu 10.10 this can be done with ```
rm $HOME/.config/gnome-session/saved-session/*
```Or, alternatively, you can cd to saved-session and remove the .desktop file containing your session-saved window manager.

---

### Post by zaenal on 2011-06-03
> **scarybeast said:**
> ...
For me it worked to clean the saved session. For Ubuntu 10.10 this can be done with ```
rm $HOME/.config/gnome-session/saved-session/*
```Or, alternatively, you can cd to saved-session and remove the .desktop file containing your session-saved window manager.

Worked very well on my Ubuntu 10.04 LTS.
Thanks :)

---

