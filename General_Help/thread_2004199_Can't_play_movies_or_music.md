---
title: "Can't play movies or music"
date: 2012-06-15
forum: General Help
---

### Post by web250 on 2012-06-15
I recently upgraded to 12.04 (full install). Initially my audio and video were working fine, but they recently stopped.

If I play an mp3 in Rhythmbox or Clementine they hang and force close. I also can't play videos in Totem/mplayer/vlc.

I even tried re-installing my root directory, to no luck. I have medibuntu repos installed, as well as w64codecs, restricted-extras, etc.

Is this an issue with the new -025 kernel? Or something else?

---

### Post by Frogs Hair on 2012-06-15
To watch movies I had to install thie following package  from medibuntu . This package was not required for playing music.  I have all the Gstreamer packages installed which are part of the restricted extras and include mp3 + mp4 codecs.  ```
sudo apt-get install libdvdcss2
```FAQ: [http://code.google.com/p/clementine-player/wiki/FAQ](http://code.google.com/p/clementine-player/wiki/FAQ)

---

### Post by web250 on 2012-06-15
> **Frogs Hair said:**
> To watch movies I had to install thie following package  from medibuntu . This package was not required for playing music. I use I have all the Gstreamer packages installed witch are part of the restricted extras and include mp3 + mp4 codecs.  ```
sudo apt-get install libdvdcss2
```

mp4 videos are the ones not working (I believe this is a separate bug).

But why would mp3s play fine (with all codecs installed), and then stop working after the most recent updates?

---

### Post by philinux on 2012-06-15
> **web250 said:**
> mp4 videos are the ones not working (I believe this is a separate bug).

But why would mp3s play fine (with all codecs installed), and then stop working after the most recent updates?

Start one of the apps in question from a terminal. Post back any errors displayed.

---

### Post by Adrian98 on 2012-06-15
Meh... have you tried to test on vmware station, if the problem persists that means there would be some limitations left in your upgrade to 12.04!

---

### Post by web250 on 2012-06-15
> **philinux said:**
> Start one of the apps in question from a terminal. Post back any errors displayed.

The error I'm getting in Clementine is:

"jack server is not running or cannot be started"

In Rhythmbox:
"** (rhythmbox:7641): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed"

---

### Post by philinux on 2012-06-15
That seems to be an ubuntuone problem with sync.

Try rebooting. And check ubuntuone.

---

### Post by web250 on 2012-06-15
> **philinux said:**
> That seems to be an ubuntuone problem with sync.

Try rebooting. And check ubuntuone.

I purged ubuntuone, restarted, and voila, my music is back.

mp4 videos work again too. 

Obviously this is a bug that needs to be fixed, but removing UbuntuOne (which I don't use anyway) is an easy enough workaround.

---

### Post by web250 on 2012-06-22
This problem has popped up again. Clementine/Rhythmbox hang when trying to play music. Totem/mplayer can't play video either

---

### Post by web250 on 2012-06-22
So it appears the issue here is that I have no audio devices showing up at all.

---

