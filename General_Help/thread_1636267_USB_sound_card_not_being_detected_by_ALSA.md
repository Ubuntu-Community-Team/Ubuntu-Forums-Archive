---
title: "USB sound card not being detected by ALSA"
date: 2010-12-02
forum: General Help
---

### Post by crosstalk45 on 2010-12-02
Hello everyone, I'm having an issue with my USB soundcard and ALSA. The system seems to detect the card when I run "lsusb" and run "cat /proc/asound/cards". However, when I try to run "sudo alsaconf" the card does not appear. I tried to edit .asoundrc directly and use the id of the card (0, which comes up under /proc/asound/cards), and it does appear in alsamixer after.  The card also appears in kmix, and allows me to change the volume.

However, when I try to run Audacity, I cannot select the USB card as a playback device, but I can select it as a recording device. When I try to play a mp3 or watch a video on YouTube, there is no audio.

Does someone know how to properly configure a USB soundcard with ALSA? I'm running ALSA 1.0.22 by the way, and the USB soundcard is from C-Media Electronics with id 0d8c:000c. I'm running Lucid with the latest updates as well. Any help would be appreciated. Thanks.

---

### Post by crosstalk45 on 2010-12-03
Bump for more people to notice.

---

### Post by crosstalk45 on 2010-12-04
Bumping one more time.

---

