---
title: "How can I have a splash screen on shutdown?"
date: 2010-06-21
forum: General Help
---

### Post by GeoMX on 2010-06-21
I'm working on a "custom" Karmic installation, I start with a debootstrap system and then install some other packages (xorg and fluxbox, mainly). The system runs quite well, but I'd like to be able to have a splash screen when the system shuts down. I have usplash installed, and it appears correctly when the system starts, but it never shows when it is shutting down.

Does anyone know where/how is usplash launched on shutdown, or where could I find this information?

Or any other splash software that you'd recommend? I'm just about to try splashy ;).

Thanks in advance for all of your help.

---

### Post by acrazyplayer on 2010-06-21
To be honest I'm not exactly sure however I know I have seen many shutdown scripts before so maybe you can turn the startup into a shutdown one. I think Google is your best friend here.

---

### Post by GeoMX on 2010-06-22
Could not install splashy because of this bug: [https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089](https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089)

I had a deeper look at usplash inner workings and managed to solve my problem, usplash appears on shutting down now :). 

Thanks.

---

