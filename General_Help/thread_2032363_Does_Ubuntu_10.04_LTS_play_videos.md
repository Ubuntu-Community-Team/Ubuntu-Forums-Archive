---
title: "Does Ubuntu 10.04 LTS play videos"
date: 2012-07-23
forum: General Help
---

### Post by jacatone on 2012-07-23
Tried Linux Mint but it doesn't play different video formats. Does Ubuntu play video formats. Seems strange since WinXP will play everything with K-Lite installed. Thanks.

---

### Post by papibe on 2012-07-23
Hi jacatone.

Similar to Windows, Ubuntu will play anything you can a find a CODEC for it.

Some video formats  are not installed by default (licence restrictions), but they can be easily added afterwards.

In my understanding, this should be also the case with Linux Mint.

Let us know hot it goes.
Regards.

---

### Post by GreatDanton on 2012-07-23
If you don't want to manually install codecs then you can install Vlc, which contains all possible codecs.

Hope this helps.

---

### Post by jacatone on 2012-07-24
No, VLC doesn't solve the problem. In Windows, just downloading and installing the latest version of K-Lite will allow me to play everything from Quicktime to mkv. Is there an all-in-one file out there for Ubuntu as well?

---

### Post by papibe on 2012-07-24
Try this:
```
sudo apt-get install ubuntu-restricted-extras
```
Then follow this guide to install ffmpeg with aac support: [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+aac").

Regards.

---

