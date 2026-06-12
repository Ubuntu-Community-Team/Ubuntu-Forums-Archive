---
title: "mic echo"
date: 2010-02-17
forum: General Help
---

### Post by infix26 on 2010-02-17
hello,

i just installed the latest ubuntu on my thinkpad laptop. everything works great, except my integrated microphone.
it works, but unfortunately there is annoying echo. i noticed this problem first when i used skype. but, apparently the problem is not due the skype setting since the same echo problem i also experienced when i used sound recording.

does anyone have this problem before? how to get rid of this mic echo problem.

thanks!

---

### Post by infix26 on 2010-02-17
hello,

i just installed the latest ubuntu on my thinkpad laptop. everything works great, except my integrated microphone.
it works, but unfortunately there is annoying echo. i noticed this problem first when i used skype. but, apparently the problem is not due the skype setting since the same echo problem i also experienced when i used sound recording.

does anyone have this problem before? how to get rid of this mic echo problem.

thanks!

---

### Post by cariboo on 2010-02-18
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by infix26 on 2010-02-19
Problem SOLVED! ;)

Use ALSA and remove Pulseaudio:

sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
(then logout and login again -- Alsamixer is used to adjust volume)

to get Pulseaudio back:
sudo apt-get install ubuntu-desktop

Source:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1368141&page=2](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1368141&page=2)

---

