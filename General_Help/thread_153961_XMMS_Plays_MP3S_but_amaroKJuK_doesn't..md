---
title: "XMMS Plays MP3S but amaroK/JuK doesn't."
date: 2006-04-02
forum: General Help
---

### Post by deltablaze on 2006-04-02
Ok, I've been using the forum search function, pasting commands into the terminal all day but this is really bugging me. First of all I should let you know I'm using Drake drapper or whatever you guys call it, lol. Anywho, I can play mp3s with XMMS, but with JUK and/or amaroK they simply don't play. 
Its just I don't want to have to use XMMS as amaroK has features XMMS doesn't.
Thanks, help much appreciated. :) ](*,)

---

### Post by duffydack on 2006-04-02
think you need amarok-xine engine installed...
i prefer xmms, as its closer to winamp.  also the sound/EQ aint as good for me.

---

### Post by deltablaze on 2006-04-02
Thanks for your reply, but the problem is I've installed that and it still doesn't work. Unless, I'm meant to be running a different amarok other than the one thats in the Multimedia list on the menu?

---

### Post by duffydack on 2006-04-02
sorry then i dont know.  im not a big fan of amarok tbh..  dont like the media library way of managing my music.....

---

### Post by deltablaze on 2006-04-02
Yeah, I Just found how XMMS has a playlist (didn't think it actually had that) and its looking great now, really like Winamp which is what I Used on Windows.

---

### Post by duffydack on 2006-04-02
with a good skin and imported winamp EQ settings its a close enuff winamp clone for me... Whats most important is the EQ settings, they are exactly the same in xmms/winamp and they sound the same too.. amarok using the EQ with presets in that drops the volume so low that when i adjust system volume to compensate a system sound blows my head off...  they also dont sound the same even after volume adjustment.. i have played with the EQ but nothng makes any difference, also Im no good with EQ settings really, and i have crap speakers, so i need eq presets, they make the world of difference to me..   just my 0.02p

---

### Post by Neo Ex on 2006-04-02
I did this and I can play mp3s in amaroK without problems: I installed 'gstreamer0.8-mad' (and all the gstreamer0.8-plugins), and then I run 'gst-register-0.8' from the terminal. I use amarok-xine and it works.

---

### Post by sinaen on 2006-05-25
done all this but still not a sound from amarok

---

### Post by ace2005 on 2006-05-25
Well for MP3 and Juk all i had to install was Juk, and everything synaptic came up with in a search for "libarts" and make sure juk outputs to arts via Settings > Output To > aRts.

As for amarok (i don't use it but i know it works) i also use the xine engine with output set to alsa

---

### Post by Jucato on 2006-05-25
By any chance have you installed the libxine-extracodecs? Because Dapper and Breezy have different requirements to play MP3s. Have you followed the instructions on this page: [https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)
(take note of the Drapper specific instructions)

Also, check if you're using the proper engine (Xine) and check if they're set up properly. I'm not sure, but GStreamer might not be working under Dapper.

Other than that I'm a bit clueless. I'll try running Dapper Live CD tomorrow and try to set it up to play MP3s.

---

### Post by faswad on 2006-05-25
```
sudo apt-get libxine-extracodecs
```

Open Amarok.
Under the Settings > Configure Amarok > Engine > Sound System, select Xine.

Close and re-open Amarok.

---

### Post by warp99 on 2006-05-26
If your using GStreamer you need the akode packages for aRts:

sudo apt-get install akode akode-mpeg

---

### Post by CitizenKane on 2006-05-28
I am a fan of amarok and I did manage to get it working with mp3s, to be honest i am not entirely sure how.  First make sure that you have the w32codecs package installed.  Also, just try the following to make sure you have everything, it certainly doesn't hurt.  This is done in with Konsole of course.

```

sudo apt-get update
sudo apt-get install amarok-arts amarok-engines amarok-xine libmad0

```

I have often noticed that the absence of libmad (mpeg audio decoder) causes amarok not to work as I am pretty sure it requires it.  I'd say it's worth a try.

---

### Post by DarkStarDeity on 2006-06-08
Installing libxine-extracodecs allowed me to play mp3s in amarok and totem. *But* - it killed the sound on streaming videos through the totem-xine firefox plugin, and did nothing to fix juk. So I rolled back since I don't much like amarok and would prefer to use juk, or failing that, madman for maintaining my music library. The totem player itself is flakey (crashes on startup) although the FF plugin seems to work fine, so I think I'll be using VLC for videos :)

---

