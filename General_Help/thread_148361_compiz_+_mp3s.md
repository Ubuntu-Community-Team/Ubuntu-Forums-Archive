---
title: "compiz + mp3s"
date: 2006-03-21
forum: General Help
---

### Post by sleepkreep on 2006-03-21
Hello, I just got XGL/compiz working with KDE the way I like it with the exception of my music collection.  I cannot play any audio files in Amarok, Juk, Kaffeine, or any KDE multimedia player for that matter.  I can seem to play videos just fine and can play audio files with any GNOME app.  Has anyone had this problem and/or have a solutiong?

---

### Post by benvdh on 2006-03-22
Hey,

You could try having a look in the KDE Control Center > Sound and Multimedia > Sound system. Then click the hardware tab, and select Threaded Open Sound System as the "Select the audio device" option. Then apply. 

Hope this solves your problem,

Regards,

Ben

---

### Post by sleepkreep on 2006-03-22
Well the problem isn't arts since I've tried it with gstreamer and xine, both using alsa instead of arts as the output plugin.  Rhythmbox uses gstreamer (I think) and works just fine.  Actually I think the problem may be the slider widget.  I've noticed that Xgl likes to mess with sliders.  For instance, the sound mixer widget in GNOME is backwards.  If you turn the widget up, it actually turns the sound down.  Scrolling down on the widget moves the widget up.  It may be that the slider is getting screwed up and therefor screwing up playback.  But honestly this is very unlikely.  It's most likely the way the music apps are calling the different backends.  Argh, I miss my music.  Can anyone use Juk/Amarok/etc. with Xgl or am I the only one having this problem?

---

### Post by sleepkreep on 2006-03-24
Fixed..Latest CVS solved the problem

---

