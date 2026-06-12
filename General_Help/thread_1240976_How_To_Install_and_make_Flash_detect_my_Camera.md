---
title: "How To Install and make Flash detect my Camera?"
date: 2009-08-15
forum: General Help
---

### Post by TheNerdAL on 2009-08-15
I have a Logitech BuddyCam Express and Would like to be able to use it on a Xat.Com Chat, how do I make Flash Detect the Camera?

---

### Post by TheNerdAL on 2009-09-26
Anybody?

---

### Post by cprofitt on 2009-09-26
Are you using 32bit or 64bit Ubuntu?

---

### Post by gordintoronto on 2009-09-26
Does Cheese work with your camera?

---

### Post by cos85 on 2009-09-27
Does your cam appear when you do lsusb?

Assuming you have mplayer installed, when happens when you try
```
mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0:fps=30:outfmt=yuy2
```

what about
```
mplayer -cache 128 -tv driver=v4l:width=640:height=480:outfmt=i420 -vc rawi420 -vo xv tv://
```

You may have to force compatibility with v4l1 (helps with some logitech webcams). Let me know if anything above works at all, and I'll tell you what to do.

cos

---

