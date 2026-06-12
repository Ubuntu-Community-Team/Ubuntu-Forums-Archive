---
title: "No sound in vlc"
date: 2010-05-15
forum: General Help
---

### Post by praveesh on 2010-05-15
In KUbuntu lucid 64 bit, there is no sound . All other applications using phonon like amarok works well . I changed the default sound to pulse audio and alsa in vlc preference, but that didn't help .
Please help

---

### Post by praveesh on 2010-05-15
please help

---

### Post by praveesh on 2010-05-16
Bump

---

### Post by kio_http on 2010-05-16
> **praveesh said:**
> Bump

Go to KDE SYSTEM-SETTINGS
Open Multimedia.

You should see two devices, if you have one sound-card, or more if you have multiple sound cards.

Test playback for all devices. 

Then comeback to this thread and post which works and which doesn't.

---

### Post by praveesh on 2010-05-17
Turning up the volume on PCM channel in kmix Helped solving the issue. Thanks for everybody who helped me.

---

### Post by ganeshmallyap on 2010-06-28
Hi all,

I am also facing this problem.  I tried executing kmix application through menu and from konsole as well.  But the only thing I can see is a small icon on the task bar which vanishes after few seconds.  nothing more.  Not sure why.

Regards
Ganesh

---

### Post by ganeshmallyap on 2010-06-28
hi all,

I figured out now that kmix is a volume control sitting in the system tray.  I noticed the volume slider for PCM mode had hit rock bottom.  After adjusting this, now sound is working fine.  Thanks to all.

Regards
Ganesh

---

