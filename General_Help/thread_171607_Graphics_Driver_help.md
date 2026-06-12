---
title: "Graphics Driver help"
date: 2006-05-07
forum: General Help
---

### Post by SomaHoliday on 2006-05-07
I installed Ubuntu and everything seems ok when I get to something that says Server X (graphical interface) isn't working then it sends me to a command prompt. I have a Raedon 9250 videocard, what could the problem be?

---

### Post by Qrk on 2006-05-07
I'm surprised Ubuntu didn't detect that one.

Anyway, you'll have to go through the standard get X working procedure.

First use this command: 

```
sudo dpkg-reconfigure xserver-xorg
```

The second screen of the dialog will give you options to select drivers. Select "vesa," go through the rest as best you can.

Now type 

```
startx
```

to get to a GUI

Once you have a GUI up and running, its easier to follow this guide to get the right drivers for your card.

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

