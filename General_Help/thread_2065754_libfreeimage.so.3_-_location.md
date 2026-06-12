---
title: "libfreeimage.so.3 - location"
date: 2012-10-02
forum: General Help
---

### Post by Andrew F in Australia on 2012-10-02
Hi all, 

Tried multiple attempts to locate the above file, needed to get Google Earth looking native and not in a poor courier-font that does not kern well.

I am following these instructions, but the file's not in the cloud anymore.

[http://askubuntu.com/questions/41562/how-to-fix-fonts-in-google-earth-6](http://askubuntu.com/questions/41562/how-to-fix-fonts-in-google-earth-6)

Have tried terminal searches using locate, etc... no joy.

I'm at the end of my ability/experience.

Could someone please explain how to locate this file and install it as outlined above?

With many thanks in advance,

Andrew F

---

### Post by mooscape on 2012-10-05
I am having the same problem here. 

By installing libfreeimage via synaptic, and then doing a search of my files, I find libfreeimage.so.3 as a link to libfreeimage-3.15.1.so - on the other hand I don't know how to procede from here.

---

### Post by mooscape on 2012-10-05
[https://help.ubuntu.com/community/GoogleEarth#Troubleshooting](https://help.ubuntu.com/community/GoogleEarth#Troubleshooting)

scroll down to comment on 'Libfreeimage' - there appears to be a problem with bugs.

(I have re-installed as only way to get google-earth to work.)

---

### Post by Memotl on 2012-10-15
Installing 'libfreeimage3' from synaptic, and then running from terminal:

```
cd /opt/google-earth
LD_PRELOAD=/usr/lib/libfreeimage.so.3 google-earth
```

gets G-E running, updates the menu fonts and makes accessing to google account actually possible.

There's no need to run it again this way again, one time will do. Though, user session ends when you close it.

---

### Post by alienmindtrick on 2013-07-08
This worked well for me, and I thank you.

---

