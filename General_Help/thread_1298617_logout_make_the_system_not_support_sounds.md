---
title: "logout make the system not support sounds"
date: 2009-10-23
forum: General Help
---

### Post by linux-_- on 2009-10-23
hi everyone

my problem is whene i logout then login

all players do not support the sound :confused:

and the system custom sounds for buttons
(system > preferences > sound > TAB sounds)



but if i get Restart the system ... every thing be ok 


my problem is in logout and login

---

### Post by linux-_- on 2009-10-23
up
up
up

---

### Post by linux-_- on 2009-10-23
what is wrong...

is there no one can help me?

---

### Post by claracc on 2009-10-23
I have the same problem since i installed jaunty 9.04 last June.
I fix the problem running the following commands in a x-term:
sudo alsa force-reload
pulseaudio -D
And the sound comes back
I think it is a bug in pulseaudio software.

---

### Post by linux-_- on 2009-10-24
thanks man it's work

---

