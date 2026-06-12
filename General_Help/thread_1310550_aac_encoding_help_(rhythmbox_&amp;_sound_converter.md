---
title: "aac encoding help (rhythmbox &amp; sound converter)"
date: 2009-11-01
forum: General Help
---

### Post by ocnvnu318 on 2009-11-01
under sound converter and rhythmbox I'm trying to be able to convert audio into AAC, but there is no choice for AAC. (I'm running Jaunty if that makes any difference)

under rhythmbox I can select .flac, .ogg, .mp2, .wav, and .spx
under sound converter I can select .ogg, .flac, or .wav

I would like to be able to select AAC for converting CDs in Rhythmbox, and AAC for converting MP3s in sound converter. What must I do in order to be able to select AAC? and also is there anyway to convert files that are already in rhythmbox to another format? I'm using sound converter because I couldn't find a way, but I figure I'll ask just in case I overlooked something.

thanks!

---

### Post by ocnvnu318 on 2009-11-02
help please? I have installed the plugin for playing AAC as my files play just fine, but I cannot convert. Under rhythmbox I have an AAC audio profile, but I cannot choose it under preferred formats.

thank you

---

### Post by ocnvnu318 on 2009-11-02
anyone? how do I get AAC encoding working?

---

### Post by mc4man on 2009-11-02
Don't use either but you'll need  at least libfaac0

gstreamer apps seemed to be also intertwined with the plugins so maybe just run this (will pull in libfaac0 if not already installed

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```

---

### Post by ocnvnu318 on 2009-11-02
thank you so very much! worked like a charm, I didn't realize the variants of the gstreamer plugins, I did not have the multiverse one. thank you much!

---

