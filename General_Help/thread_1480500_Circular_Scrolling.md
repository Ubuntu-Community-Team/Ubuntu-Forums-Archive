---
title: "Circular Scrolling"
date: 2010-05-11
forum: General Help
---

### Post by pantherattack on 2010-05-11
I just upgraded to Lucid on my laptop, and I noticed that the option to do circular scrolling (ie. you move your finger in a CW circle to scroll down, and CCW to scroll up)  is no longer available. I tried to search for a solution, but I didn't know what to call it besides "circular scrolling".

Does anyone know how I can get this back?

Ian

---

### Post by DomesDKG on 2010-05-11
You might try getting the newer version of gpoiting. For some reason Lucid only has 1.3.2, but you can install the debian version of 1.5.1 and it works great. Fixed my touch pad problems on my Thinkpad.

You can get the download files for 1.5.1 from here:
[http://packages.debian.org/sid/libgpds0](http://packages.debian.org/sid/libgpds0)
[http://packages.debian.org/sid/gpoin...evice-settings](http://packages.debian.org/sid/gpoin...evice-settings)
I'm not sure if you need this third one, but I installed it.
[http://packages.debian.org/sid/libgpds-dbg](http://packages.debian.org/sid/libgpds-dbg)
Afterwards you can configure it in system>preferences>pointing devices.

---

### Post by pantherattack on 2010-05-12
Thanks for the response. I'm having trouble building it. The ./configure is telling me that it can't find gnome-settings-daemon. It wants version 2.28.0 or greater, and I have 2.30.1 installed, so I don't know what's up.

```
checking for GNOME_SETTINGS_DAEMON... configure: error: Package requirements (gnome-settings-daemon >= 2.28.0) were not met:

No package 'gnome-settings-daemon' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
```


Oh, and BTW, the second link was cut off a bit. It should be [http://packages.debian.org/sid/gpointing-device-settings](http://packages.debian.org/sid/gpointing-device-settings)

Ian

---

