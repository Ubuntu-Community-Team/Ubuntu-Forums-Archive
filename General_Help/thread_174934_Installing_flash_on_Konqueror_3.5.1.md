---
title: "Installing flash on Konqueror 3.5.1"
date: 2006-05-12
forum: General Help
---

### Post by Virtuous on 2006-05-12
I don't have flash on Konqueror and I was wondering if there was a way to install flash on it?

---

### Post by cgjones on 2006-05-12
I've installed it manually before. Download Flash, unpack it and copy libflashplayer.so (I think thats what its called) to the Mozilla plugins directory. Then in Konqueror, go to the plugins settings page and click Scan for plugins. I'm not at my Ubuntu computer right now, so I can't get the specifics.

---

### Post by Virtuous on 2006-05-12
Thank you! I did what you said and it works! But there is another problem. I don't have sound coming through when I watch a flash movie. Is there a way to fix that? Thank you though for helping me with the flash installation!

---

### Post by cgjones on 2006-05-12
There is some information [here](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash)  on possible fixes for the sound.

---

### Post by anschelsc on 2006-10-23
I tried this method and it found the pluggin but when I went on addicting games it gave me this error after it loaded: nspluginviewer crashed with signal 11. On backtrace it said:

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232581904 (LWP 24227)]
[New Thread -1267356768 (LWP 24231)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb6ade404 in pthread_mutex_lock ()
   from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb79b2be6 in pthread_mutex_lock () from /lib/tls/i686/cmov/libc.so.6
#8  0xb60fd9f8 in NP_Shutdown ()
   from /home/anschel/.mozilla/plugins/libflashplayer.so
#9  0xb6141362 in NP_Shutdown ()
   from /home/anschel/.mozilla/plugins/libflashplayer.so
#10 0xb600be3d in NP_Shutdown ()
   from /home/anschel/.mozilla/plugins/libflashplayer.so
#11 0xb5f7f568 in ?? () from /home/anschel/.mozilla/plugins/libflashplayer.so
#12 0xb5f77130 in ?? () from /home/anschel/.mozilla/plugins/libflashplayer.so
#13 0xb657c780 in ?? () from /home/anschel/.mozilla/plugins/libflashplayer.so
#14 0xb657c1e0 in ?? () from /home/anschel/.mozilla/plugins/libflashplayer.so
#15 0xbfb492f8 in ?? ()
#16 0xb64d7c9a in ?? () from /home/anschel/.mozilla/plugins/libflashplayer.so
#17 0xb64d7c84 in NP_Shutdown ()
   from /home/anschel/.mozilla/plugins/libflashplayer.so

```

no idea what may have caused this. clearly it recognized the plugins because of the last bit (with /home/anschel/.mozilla/plugins/libflashplayer.so) but beyond that no idea

---

### Post by LightsOut on 2006-10-31
im getting the same error as the guy above. Any ideas?

---

### Post by LightsOut on 2006-10-31
to get it to work do this:

> **Flamekebab said:**
> ```
sudo gedit /etc/X11/xorg.conf
```

Then scroll down to near the bottom of the file and change:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
```
to:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    **_*24*_**
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
```

Of course, yours may be slightly different, as you'll probably not have the same monitor and graphics card as me, but you get the idea, I hope.

---

