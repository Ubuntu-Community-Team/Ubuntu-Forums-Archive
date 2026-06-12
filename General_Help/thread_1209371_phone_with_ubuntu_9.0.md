---
title: "phone with ubuntu 9.0"
date: 2009-07-10
forum: General Help
---

### Post by asliyanage on 2009-07-10
is it possible to use my sony erricson k770i phone with ubuntu 9.0 or  should  i need to install another plugin ?

---

### Post by m4tic on 2009-07-10
I use w880i, just connect and loads, only network and file transfer work though. not phone mode

---

### Post by t0p on 2009-07-10
Have you tried connecting the phone to the computer?

I've found with sony ericsson phones (I currently use a K800i) that if I connect the phone to computer via usb data cable, the phone displays a menu where I can choose Phone Mode, File Transfer and Print.

Phone Mode allows me to use the phone functions such as modem.  File Transfer allows transfer of files - music, images, etc.  I don't use a printer so I haven't tried the Print mode, but I believe it is a HP utility.

---

### Post by wojox on 2009-07-10
Connect with usb and open Rhytmbox for music.
Do you have memory stick card in phone?

---

### Post by asliyanage on 2009-07-10
is there any 3gp converter in ubuntu  default?

---

### Post by wojox on 2009-07-10
Download wine and [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

---

### Post by t0p on 2009-07-10
> **asliyanage said:**
> is there any 3gp converter in ubuntu  default?

It's been a while since I played a .3gp file.  But if memory serves me correctly, I believe you can play .3gp video with **mplayer** with no need for conversion, if you install the correct codecs.  Ubuntu-restricted-extras has them:

```
sudo apt-get install ubuntu-restricted-extras
```

I expect **ffmpeg** can convert them to other formats.  But ubuntu won't do this "by default" as ubuntu doesn't handle proprietary formats "out of the box".

---

