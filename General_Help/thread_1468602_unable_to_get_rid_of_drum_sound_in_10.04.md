---
title: "unable to get rid of drum sound in 10.04"
date: 2010-05-01
forum: General Help
---

### Post by tommyboy808 on 2010-05-01
i already tried getting rid of the gnome log in sound in system>preferences>startup applications

as well as disabling sounds in system>preferences>sounds>no sounds

as well as typing sudo -u gdm gconftool-2 –-set /desktop/gnome/sound/event_sounds –-type bool false in terminal, i even checked in gconf-editor to see that the event sounds has been disabled

however, that drum sound (da da) still plays when ubuntu loads.  any suggestions on other ways to disable or remove it?  

in karmic sudo -u gdm gconftool-2 –-set /desktop/gnome/sound/event_sounds –-type bool false this was what worked for me.  but it isnt working in 10.04?

---

### Post by wojox on 2010-05-01
Try going to System > Preferences > Startup Applications and remove it. 

You could always go into Sounds and disable all sound.

---

### Post by tommyboy808 on 2010-05-01
uhm i thought i said i tried that dude :(

---

### Post by todak on 2010-05-01
Open gconf-editor. Drill down to */apps/gdm/simple-greeter/settings-manager-plugins/sound* and see if the *active* box is unchecked.

---

### Post by tommyboy808 on 2010-05-01
hey todak, thnx for trying but still doesnt work :(

---

### Post by todak on 2010-05-01
How about *System> Administration> Login Screen*. Click the *Unlock* button, enter your password and then uncheck the *Play login sound* box and see if that works. If that does not work, then I am stumped. :confused:

---

### Post by tommyboy808 on 2010-05-01
wow todak, you are the man!!!! thnx worked perfectly, can't believe i didnt see that

---

### Post by todak on 2010-05-01
> **tommyboy808 said:**
> wow todak, you are the man!!!! thnx worked perfectly, can't believe i didnt see that

Glad I could help! Please mark the thread as "SOLVED" so that others will know that a solution has been found if they had a similar question.

---

