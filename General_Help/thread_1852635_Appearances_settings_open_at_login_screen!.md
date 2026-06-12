---
title: "Appearances settings open at login screen!"
date: 2011-09-30
forum: General Help
---

### Post by OxentroT on 2011-09-30
Hello!
       I recently had to change some policies on my laptop before I traveled so that a disclaimer appears at login whenever the terminal is powered on. I forgot that I had replaced login background with this disclaimer (warning page) a few month ago. And now the appearances window opens every time the terminal is powered on.

I forgot what exact steps that I had taken to be able to change the background and was wondering if anyone would know off the top of their head how I can change this so the appearances window does not open every time the machine is powered on and displays at login.


Thank you for any help in advance!

:guitar:

---

### Post by Krytarik on 2011-09-30
Just run this command to remove the Appearance dialog from GDM's login screen startup:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```Greetings.

---

### Post by OxentroT on 2011-09-30
Thankyou very much! I had stumbled upon this command some time after making this post I am sorry to have to say. I recognized it the instant that I had layed eyes on it. Must have been very busy the day I changed the setings and forgot to recall the link! 

Thanks again!

and as always, rock on.

---

