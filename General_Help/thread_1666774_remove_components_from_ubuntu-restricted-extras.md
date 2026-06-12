---
title: "remove components from ubuntu-restricted-extras"
date: 2011-01-14
forum: General Help
---

### Post by kanishkdudeja on 2011-01-14
hey..i need only some packages of ubuntu-restricted-extras.

i just want the audio and video plugins.

i dont want open jre and all dat stuff.

how can i install only some packages out of the full ubuntu-restricted-extras package ?

---

### Post by nothingspecial on 2011-01-14
```
sudo apt-get install gstreamer0.10-plugins-ugly  gstreamer0.10-plugins-bad  gstreamer0.10-ffmpeg  gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libavcodec-extra-52 libmp4v2-0 
```

Should cover it (just about).

---

### Post by kanishkdudeja on 2011-01-14
dont i need libmpeg ?

---

### Post by nothingspecial on 2011-01-14
libavcodec-extra-52 should pull that in (I think, try it)

---

### Post by kanishkdudeja on 2011-01-14
okay il try it. are u sure il be able to play flv's , avi's and mpeg's after installing all these packages ?

---

### Post by nothingspecial on 2011-01-14
I forgot the flash

```
sudo apt-get install flashplugin-installer
```

I was thinking just music and video, I forgot about flash on the web :P

---

### Post by nothingspecial on 2011-01-14
You could just follow this

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by kanishkdudeja on 2011-01-14
thanks. :)

---

