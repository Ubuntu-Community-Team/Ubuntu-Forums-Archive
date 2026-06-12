---
title: "Installin Ubuntu 5.1o in Acer TravelMate 8200"
date: 2006-04-21
forum: General Help
---

### Post by adinugro on 2006-04-21
I have problem installing ubuntu on my new laptop Acer TravelMate 8200. The VGA and network are not detected. Anyone can help???

I can install it but could not get the X windows working. How di I setup the VGA in text mode?

I tried install driver from ATI but was not success.

Many Thanks!

---

### Post by btnheazy03 on 2006-04-21
VESA is more widely supported, keep that in mind
For instance when I tried installing SuSE 10.0 OSS,  X server won't start, but when I pressed F3 and switched to VESA mode it went on without a hitch.

If you're stuck in command line try

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by adinugro on 2006-04-23
Many thanks. It works now, using vesa. I am going to try to install ATI driver later on.

---

