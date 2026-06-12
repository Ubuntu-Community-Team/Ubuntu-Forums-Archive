---
title: "sound broken for one user only"
date: 2009-12-21
forum: General Help
---

### Post by itlarson on 2009-12-21
My sound is currently broken- but only for one user loggin.  Rebooting and Alsamixer fiddling haven't helped.  Does anyone have any idea why this might happen, or what I might try?

---

### Post by warfacegod on 2009-12-21
Have you checked to see if that users master volume is muted?

---

### Post by lisati on 2009-12-21
Have you checked their ability to use audio devices in System->administration->users & groups?

---

### Post by itlarson on 2009-12-26
Problem fixed!  Here's the entire saga-
  
One thing I noticed when my sound stopped working was that when I moved the master volume control on the panel up and down, it had no effect on Alsamixer.  When things are working normally, the levels in alsamixer go up and down when you move this control.  Next I tried using oss with Exaile music player,which can be selected in preferences.  After restarting Exaile I had sound, which diagnosed this as an alsa or pulseaudio problem.  I could have just continued to use oss for playing music, but editing it was another story.  Audacity refused to use oss, giving an error dialog.  I could get sound from it if I selected a different alsa sound output in preferences, but it would play only one channel at a time in alternating two second intervals.  Another problem was sound in flash.  Mozilla uses a alsa pluggin, so sound wasn't working here either. 
     I used to use kde 3.5 exclusivly, so I was unaware you can get a sound settings dialog in xfce (and gnome?) by right clicking on the master voume control.   Once I discovered this I immediately noticed sound was being routed to my usb phono pre-amp instead of the on-board intel sound hardware.  All I had to do was select the intell hardware for sound output.  Once I changed audacity back to the default alsa output, and changed exaile back to alsa and restarted it, my sound was working normally. Flash sound just worked, since I hadn't changed anything having to do with it.
      I still don't know why this happened.  I didn't do anything to cause it.  Xfce user switching seems to cause sound bugs sometimes.  Or maybe it was just another result of the ongoing war between alsa and pulseaudio.

---

