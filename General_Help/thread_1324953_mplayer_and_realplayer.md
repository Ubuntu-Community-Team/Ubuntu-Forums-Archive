---
title: "mplayer and realplayer"
date: 2009-11-13
forum: General Help
---

### Post by weishigoname on 2009-11-13
when I want to watch techwise tv on cisco network website.In windows xp ,I can select which player---realplayer or windows media player, to player the video.but when I use ubuntu ,I can not select----there are not select options.and mozilla firefox select automatically for me ----it select mplayer,which can not player correctly,only voice,not image .how can I do than can let me select realplayer to play the video ?

---

### Post by running_rabbit07 on 2009-11-13
I don't know how to set it up to switch, but if you haven't installed the codecs, you should do it now. ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by fluffman86 on 2009-11-13
Do you have all of the necessary codecs installed?

Go to System > Administration > Software Sources and make sure the top 4 boxes are checked.  

Then open Applications > Ubuntu Software Center and search for Ubuntu Restricted Extras and install that.

If that fails, go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and add that repository.  Afterward you'll be able to install realplayer or w32codecs which may help.

---

### Post by weishigoname on 2009-11-15
thanks

---

### Post by 6205 on 2009-11-15
I don't understand one thing. Why are so many users ignoring default Totem movie player with default totem-mozilla-plugin and instead of that are fighting with mplayer, gnome-player, realplayer, vlc-mozilla or other s*it. 

There is simply nothing better than default totem-mozilla-plugin.
You need only install all necessary GStreamer plugins like ->

gstreamer-plugins-bad
-bad-multivers
-ugly
-ugly-multiverse
-ffmpeg
-pitfdll
-w32codec (available in medibuntu repository)

---

### Post by running_rabbit07 on 2009-11-15
> **6205 said:**
> I don't understand one thing. Why are so many users ignoring default Totem movie player with default totem-mozilla-plugin and instead of that are fighting with mplayer, gnome-player, realplayer, vlc-mozilla or other s*it. 

There is simply nothing better than default totem-mozilla-plugin.
You need only install all necessary GStreamer plugins like ->

gstreamer-plugins-bad
-bad-multivers
-ugly
-ugly-multiverse
-ffmpeg
-pitfdll
-w32codec (available in medibuntu repository)

Choice. Freedom. Opinion. Every time I used totem, it had to uninstall the plugins it was using to download a different one. VLC is the bomb-diggity.

---

