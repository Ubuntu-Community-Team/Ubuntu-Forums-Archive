---
title: "Black Screen After Resume from Sleep/Suspend"
date: 2011-12-20
forum: General Help
---

### Post by user1397 on 2011-12-20
I installed kubuntu 11.10 on my gateway laptop, and everything seems to work pretty nicely except for suspend, which is a pretty big problem for me.

I have already tried using these three kernels:

linux-image-3.0.0-12
linux-image-3.0.0-13
linux-image-3.0.0-14

All of them give the same result.

I think I saw a bug report on launchpad that descirbed this same situation but it concerned only the 3.0.0-15 kernel, while mine concerns any kernel it seems.

---

### Post by maverickaddicted on 2011-12-20
I also face the same problem, screen goes blank after resume. To get back the login screen, I have to press ctrl+alt+f1 and restart the gdm process by following command
```
sudo service gdm restart
```. 
However, it closes all the open applications and all the unsaved data is lost.
My kernel version is 3.0.0-14-generic. I also don't know why this happen?

---

### Post by jc3835 on 2011-12-21
I'm also experiencing this, with Ubuntu Unity. Not sure if it's also doing it using a fallback Gnome session.

Also happens anytime I switch users and log in with a second user; I then can't switch back without getting the black screen.

---

### Post by user1397 on 2011-12-24
bump

---

