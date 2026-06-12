---
title: "Can't play WMV files in Ubuntu 10.04"
date: 2010-05-02
forum: General Help
---

### Post by jacatone on 2010-05-02
Installed the w32 codecs in Ubuntu 10.04, but can't get the video to work in either Mplayer or VLC. Audio works OK, though. Anyone know how to fix this? Thanks.

---

### Post by spiky001 on 2010-05-02
What player are you using? VLC covers most things

---

### Post by WorMzy on 2010-05-02
You may need to install or update propriety drivers for your graphics card. I had a similar problem, but with all video files, updating my video drivers to the most recent version fixed the problem.

---

### Post by jacatone on 2010-05-02
The video driver may be the problem. Ubuntu said there was an Nvidia 96 accelerated driver available, but when I installed it my resolution stopped at 640x480 and I couldn't fix it. So, I just used the generic video driver that comes with Ubuntu.

---

### Post by Ugurcan377 on 2010-05-02
have you tried
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by km0r3 on 2010-05-02
I had the same problem. Follow the instructions on Ubuntu Geek:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html)

---

### Post by techunit on 2010-05-02
> **Ugurcan377 said:**
> have you tried
```
sudo apt-get install ubuntu-restricted-extras
```


This is correct or you can search restricted extras in Ubuntu Software explorer

---

