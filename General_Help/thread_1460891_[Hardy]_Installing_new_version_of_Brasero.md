---
title: "[Hardy] Installing new version of Brasero"
date: 2010-04-23
forum: General Help
---

### Post by TheSixthPandava on 2010-04-23
After Brasero kept crashing on startup with message:

> marko@marko-desktop:~$ brasero
Segmentation fault

i decided to try to install newer version. After installing newest gstreamer, which I was asked, the same message appears again:

> checking for BRASERO_GSTREAMER... configure: error: Package requirements (	gstreamer-0.10 >= 0.10.15			gstreamer-interfaces-0.10				gstreamer-plugins-base-0.10 >= 0.10.0) were not met:

No package 'gstreamer-interfaces-0.10' found
No package 'gstreamer-plugins-base-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BRASERO_GSTREAMER_CFLAGS
and BRASERO_GSTREAMER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


What could this be? gstreamer-plugins-base-0.10 is installed, while gstreamer-interfaces-0.10 I can't find.

How could this

> Alternatively, you may set the environment variables BRASERO_GSTREAMER_CFLAGS
and BRASERO_GSTREAMER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

be implemented?

---

