---
title: "ALSA Issues with USB Mixer"
date: 2010-12-09
forum: General Help
---

### Post by crosstalk45 on 2010-12-09
Hello  everyone, I'm having an issue with my USB mixer and ALSA. Previously I had used the latest version of OSS (from the repository), but it ended up not working so well with the microphone. So, I purged oss and installed ALSA. The USB mixer was not immediately recognized by ALSA. I had to edit .asoundrc to set it to the right card number.

The USB mixer comes up in alsamixer, and it is detected by lsusb and aplay -l. When I use Audacity, the mixer can be selected under recording devices, but not playback devices. Also, when I use vlc, there is an error where it says an oss device cannot be opened (which I thought I had removed). I don't any sound from any of these programs.

However, when I run sudo alsa force-reload, the errors disappear, and I can select a playback device in Audacity. I still don't hear any sound though. When it reboots, it goes back to the problems I had before. So, I guess I have three questions: 

How can I store the settings that force-reload change permanently? How can I completely remove OSS and ensure that only ALSA is being used? Also, how can I properly configure a USB mixer with ALSA; am I missing something?

Thanks.

---

### Post by crosstalk45 on 2010-12-09
Bumping for more people to notice.

---

