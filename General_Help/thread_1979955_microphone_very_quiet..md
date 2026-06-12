---
title: "microphone very quiet."
date: 2012-05-14
forum: General Help
---

### Post by Pacopag on 2012-05-14
Hi.  I'm trying to use skype, but the (built-in laptop0 microphone is really quiet.  I have to talk really loud and directly into the mic in order for anyone to be able to hear me.

The problem is not with skype, because if I do 
$ arecord test.wav
the playback is really quiet too.

If I go to "Volume Control" settings I get
"Error, you need to install a application to configure the sound"

I've had the same problem in Crunchbang where I think I was using Alsamixer to configure sound.  But I was never able to fix the problem in Crunchbang.

---

### Post by Pacopag on 2012-05-14
I installed pavucontrol...it didn't work, crashed on startup.

I installed alsamixer...it worked fine, but my "Capture" volume is maxed.

Maybe I need a different sound driver?  Is there a way to replace the native driver with the proprietary audio driver (i.e. the one for windows)?

---

### Post by Pacopag on 2012-05-14
Got it working better.  Still not super loud, but definitely loud enough for it to be usable.

-installed alsamixer
-maxed "Capture" and "Digital"

I also noticed the "gnome-alsamixer".  The description makes it sound pretty good, but I didn't install it because it had a couple dozen dependencies (alsamixer had only one).  Does gnome-alsamixer offer anything that might make me wet my pants?

---

