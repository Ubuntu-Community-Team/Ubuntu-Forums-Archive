---
title: "Can you increase my volume?"
date: 2009-08-25
forum: General Help
---

### Post by jesuisbenjamin on 2009-08-25
Hello Mr. Ubuntu,

My main audio volume is up to the max, my player's volume too and so is the volume of my headset. Yet my ears are not bleeding.

How can i increase the volume of my laptop so i can enjoy music better?

Thank you.

---

### Post by jheaton5 on 2009-08-25
Try this, if you haven't already.

Right click on volume control icon.
Select "Open Volume Comtrol"
Make sure all your controls are set to the max except the mic control.  Setting this control to the max may be causing the problem.

---

### Post by P4man on 2009-08-25
if he uses pulse, that wont really help.
A quick hack, play some music, then open a terminal and type:

alsamixer -c0

then increase all the sliders using the arrow keys. You are probably looking at a PCM slider which is halfway.

---

### Post by jesuisbenjamin on 2009-08-25
The headset volume was indeed not to the max. It was silly of me.#-o

Thanks, i liked the alsamixer thing :)

---

### Post by sundar_ima on 2009-08-25
I also noticed this problem. All the slider in the alsa mixer are at max level.

Some where i read that you can increase ubuntu volume up to 300% but forgot the site name.

---

### Post by jesuisbenjamin on 2009-08-25
helping people to commit audio-suicide is an offence :)

---

### Post by macogw on 2009-08-25
You could increase the gain...if you want to blow out your speakers... (assuming you're not referring to the bug where it's always at whisper-levels)

---

