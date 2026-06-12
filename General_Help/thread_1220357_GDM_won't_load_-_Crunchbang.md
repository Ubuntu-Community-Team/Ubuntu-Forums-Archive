---
title: "GDM won't load - Crunchbang"
date: 2009-07-22
forum: General Help
---

### Post by plr4ever on 2009-07-22
So after days of endless formatting, reinstalling, and repartitioning of Sabayon linux and windows 7, i decided to just go back to ubuntu (sort of).

Well after a few hours of tuning the system to my preferences, i reboot, and instead of being greeted by a login screen, i just get the default gnome loading cursor that spins around and flickers occasionaly. the only remedy i have found for this is to open a tty terminal and kill gdm, and then restart it.

Does anyone know how i might be able to reset GDM, or if that is even my problem?

Thanks!

---

### Post by demonoidmaster on 2009-07-22
Ok.

1st - Check In [ Start , System , Administration , Login Window] --- [Or Run - "sudo gdm"]

2nd - In The GDM Settings Go To The "Local" Tab, Then Under That.. Select

-Themed With Face Browser
-Selected Only
-Make Sure You Pick A GDM Theme, Then Close


Then Log Off And Try Again

---

### Post by plr4ever on 2009-07-22
It worked! Thanks!

I must have screwed something up changing the theme.

---

### Post by demonoidmaster on 2009-07-22
Happy To Hear That ;)

Well If You Ever Need Something Or Any Other Problems/Questions

Feel Free To Ask Me, Ok :)

---

