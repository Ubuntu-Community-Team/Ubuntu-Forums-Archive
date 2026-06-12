---
title: "Dual monitors"
date: 2009-10-10
forum: General Help
---

### Post by Vrekk on 2009-10-10
Ok so I got a new monitor a few days ago (LOVING IT) and my old was is just sitting here taking up space.  I the other day I though of a good use for it.

If possible I want it set up so that I have X running on one monitor and have my tty?'s running on the other one.  Dose anyone know how I would set this up?  I dont know where to start.

---

### Post by ad_267 on 2009-10-10
Providing information about your video card would be a good place to start.

I wouldn't know how to show different TTYs on different monitors, but have you considered just having two monitors next to each other with one giant desktop? It works really well.

---

### Post by Vrekk on 2009-10-10
> **ad_267 said:**
> Providing information about your video card would be a good place to start.

I wouldn't know how to show different TTYs on different monitors, but have you considered just having two monitors next to each other with one giant desktop? It works really well.

Tired the giant desktop thing once, I didn't like it, but Ill give it another shot.

I have a Nvidia 9800 GT if that helps.

---

### Post by ad_267 on 2009-10-10
Using nvidia-settings you can select to have a separate X screen on the second monitor rather than using TwinView, but I'm not sure that you'll be able to set that screen to display a TTY. That might require editing the xorg.conf file.

---

### Post by Vrekk on 2009-10-10
Tried the seperate X server option in nvidia-settings, and did like it either (picky), but it gave me an idea.

Is there a way I could set it up to open a BASIC xserver?  Not a full blown DE but something like 
```
startx -- :1
```
 But on the other monitor.

If it helps I attached my current xorg.conf file.  It shows both screens.

---

### Post by ad_267 on 2009-10-11
It might be possible but I wouldn't know how to go about it, someone else might know though. 

When I had a second monitor I used TwinView and would often just run a full screen terminal with gnu screen running on the second monitor. If you look into screen it might be able to do what you want instead of running a tty on the second monitor.

(I'm not really being very helpful sorry :))

---

### Post by Vrekk on 2009-10-11
Np, im not asking a very easy question here.

For now Ill try the seperate X server setting in nivida-settings, but i would really appreciate it if someone could figure this out.

---

### Post by ad_267 on 2009-10-11
It looks like this might help: [http://www.xbmc.org/forum/showpost.php?p=357861&postcount=9](http://www.xbmc.org/forum/showpost.php?p=357861&postcount=9)

This person is running Compiz on the main monitor and Openbox on their second monitor. If you're using Metacity that doesn't have an --only-current-screen but you might be able to use the --display option to control which monitor it runs on.

---

