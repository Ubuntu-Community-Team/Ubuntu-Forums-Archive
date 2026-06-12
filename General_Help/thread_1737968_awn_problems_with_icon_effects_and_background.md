---
title: "awn problems with icon effects and background"
date: 2011-04-24
forum: General Help
---

### Post by l_chopin on 2011-04-24
Hi! i've installed awn but it doesn't work properly. the icons effects don't work, it's the same if i activate one or another. i've try doing everything i've read:desactivating compiz, activating compiz,etc but nothing has worked.

and it always appears a white rectangle in the awn background which looks awful. i've made you a photo which is better than my explanation: [Desktop Photo]("http://www.subirimagenes.com/imagen-pantallazo1-6302181.html")
i've try to change the colours in the personalized themes window but it hasn't worked.

Please, help!!

---

### Post by Vaphell on 2011-04-24
what is your video card? do compiz desktop effects work for you - wobbly windows and stuff?

---

### Post by l_chopin on 2011-04-24
I think the video card is 1280MB NVIDIA GeForce 8600M GT TurboCache.

No, the wobbly windows and that stuff don't work either.

---

### Post by Vaphell on 2011-04-24
do you have proprietary nvidia driver installed?
if so, what happens when you right click on desktop, pick the option about changing wallpaper and in appearance tab click advanced effects?

---

### Post by l_chopin on 2011-04-24
I have just update my nvidia drivers.

If i go to advanced effects in desktop preferences, "none" is selected, so i change it to "extra", then a window appears asking me if i want to keep the option checked and i select "yes". Then i close that window and i return to advanced effects in desktop preferences and it's checked "none" again.

---

### Post by stinkeye on 2011-04-24
From the sounds of it your only able to run Metacity as your window
manager in which case you need to turn on Metacity's compositing feature.

In the terminal
```
metacity -c
```

---

### Post by l_chopin on 2011-04-24
i've made that and it returns an error: it says i could try using the option " --replace" if i wanna change the window manager. but i dont know what i have to write with the "replace".

---

### Post by stinkeye on 2011-04-24
install wmctrl for me so I can check what window manger is actually running.
```
sudo apt-get install wmctrl
```

Then enter
```
wmctrl -m
```

eg my output when running compiz...
```
glen@MavMusic:~$ wmctrl -m
Name: compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

---

### Post by l_chopin on 2011-04-24
Ok, done. This is what appears:

Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF

---

### Post by stinkeye on 2011-04-24
In the terminal 
```
gconf-editor /apps/metacity/general/compositing_manager
```
and check that it is ticked.
Does awn still not display properly ?

---

### Post by l_chopin on 2011-04-24
I don't know why but suddenly, everything works fine!The AWN effects also work!!

Thank you both!!!

---

### Post by stinkeye on 2011-04-24
> **l_chopin said:**
> I don't know why but suddenly, everything works fine!The AWN effects also work!!

Thank you both!!!

Compiz is a compositing window manager,
Which for some reason you cant run.

Awn requires compositing to display the effects.

You need to turn on compositing in metacity for awn to display properly
when running metacity as the window manager.

**metacity -c** turned on compositing for metacity.

[COLOR="Red"]Edit[/COLOR] You mean compiz is now working also??

---

### Post by Dy1anW on 2011-10-05
Wow, thanks. That worked for me too! Everything was working fine on my laptop when I was using 10.10, but upgrading to 11.04 pretty much fracked up my settings when Unity tried to take over; took a while just to get AWN up and running again, and when it finally did, I had white backgrounds behind all docks (was, and still am using ppa; effects seemed fine though). metacity -c did the trick.

---

