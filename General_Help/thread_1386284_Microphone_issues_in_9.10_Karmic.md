---
title: "Microphone issues in 9.10 Karmic"
date: 2010-01-20
forum: General Help
---

### Post by andycastille on 2010-01-20
My laptop *does *have a built-in working microphone, but Ubuntu doesn't detect it. In the Sound settings there are Microphone 1, Microphone 2, and Line-In. I've tried all three, but none work. I have the volume up to Unamplified and the speaker volume up to 50%. What do I need to do to make it work? I use Skype a lot and I need it badly. As you see the Offline Skype logo*. Please help me!









<--* Offline Skype Logo

---

### Post by wojox on 2010-01-20
Try this thread: [http://ubuntuforums.org/showthread.php?t=1306561](http://ubuntuforums.org/showthread.php?t=1306561)

Did you also try System>Preferences>Sounds then go to the input tab and unmute the input volume and bump up that to the max

---

### Post by andycastille on 2010-01-20
> **wojox said:**
> Try this thread: [http://ubuntuforums.org/showthread.php?t=1306561](http://ubuntuforums.org/showthread.php?t=1306561)

Did you also try System>Preferences>Sounds then go to the input tab and unmute the input volume and bump up that to the max Can't. It makes loud static in the speakers.

---

### Post by Jenkins1 on 2010-01-20
If you open up a terminal window and type **alsamixer** and use the arrow keys to change the volume bars so that both the "mic" and "mic boost" channels are about half way up. 

I suggest the amplification is set to about 1cm above amplification.  Also in the mic/sound settings in skype untick the **Allow skype to adjust volumes** .

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

