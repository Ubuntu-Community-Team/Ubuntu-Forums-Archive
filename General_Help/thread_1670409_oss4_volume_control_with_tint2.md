---
title: "oss4 volume control with tint2?"
date: 2011-01-18
forum: General Help
---

### Post by LuniTux on 2011-01-18
Hello,

I was wondering if anyone knows of a way to add a volume control device to tint2. The problem then would be that it has to be able to control oss4 sound. Any Ideas?

OS

Toshiba nb205
Ubuntu 10.04 mini with
slim, openbox, tint2, wicd

oss4 (installed from [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound"))

---

### Post by thil77 on 2011-01-19
don't try it, but volumeicon support OSS.
[http://www.softwarebakery.com/maato/volumeicon.html](http://www.softwarebakery.com/maato/volumeicon.html)

But you need to compile volumeicon, to enabled the config flag '--enable-oss'.

---

### Post by thil77 on 2011-01-19
don't try it, but volumeicon 0.3 support OSS.
[http://www.softwarebakery.com/maato/volumeicon.html](http://www.softwarebakery.com/maato/volumeicon.html)

But you need to compile volumeicon, to enabled the config flag '--enable-oss'.

---

### Post by LuniTux on 2011-01-19
I was just looking at that lol. I will try it when I get home.

Thanks

---

### Post by LuniTux on 2011-01-19
I was just looking at that lol. I will try it when I get home.

Thanks

---

### Post by LuniTux on 2011-01-19
I was just looking at that lol. I will try it when I get home.

Thanks

---

### Post by LuniTux on 2011-01-19
I was just looking at that. I will try it when I get home.

Thanks

---

### Post by LuniTux on 2011-01-19
I was just looking at that. I will try it when I get home.

Thanks

---

### Post by LuniTux on 2011-01-19
I tried using volumeicon but i get the error:

```
volumeicon: alsa_backend.c:88: asound_get_volume: Assertion `m_elem != ((void *)0)' failed.
```

i also tried "wmix" and got the error:

```
wmix: mixer-oss.c:318: mixer_set_channel: Assertion `(channel >= 0) && (channel < n_channels)' failed.
```

i would think that something is wrong with my sound but i can control the sound using ossxmix. am i missing a package or something?

---

### Post by LuniTux on 2011-01-25
still have got the sound controller to work. I noticed that if I use volumeicon on a full ubuntu installation, the device works properly. I'm installing random packages now from the original install

---

### Post by LuniTux on 2011-02-02
Yay me. I found a solution... sort of

[http://ubuntuforums.org/showthread.php?t=1679754]("http://ubuntuforums.org/showthread.php?t=1679754")

---

