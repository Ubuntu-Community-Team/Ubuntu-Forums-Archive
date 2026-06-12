---
title: "How to disable boot up sound in 10.04"
date: 2010-08-10
forum: General Help
---

### Post by cforput on 2010-08-10
I want to turn off the sound when Ubuntu boots and can't figure out how. I have tried System > Preferences > Sound > making sure mute is checked for alert volume and also the alert volume level is all the way to the left. It still goes off when I boot. 

How do I stop it?

---

### Post by mike555 on 2010-08-10
uncheck it in startup applications ..

---

### Post by cforput on 2010-08-12
That didn't work but I figured it out. I went to system > Administration > Login Screen

From there, I unlocked the config (ID/PW) and there is a flag here that says "Play Login Sound". I unchecked that and rebooted to check. 

Thats what did it for me.

---

