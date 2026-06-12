---
title: "Pan - Segmentation Fault"
date: 2010-06-19
forum: General Help
---

### Post by mooreted on 2010-06-19
I have Pan on Ubuntu 10.04 at work and it works fine. Here, also running 10.04 I keep getting a segmentation fault when loading headers. The only error I get is "segmentation fault".

I have removed Pan and deleted .pan2 and reinstalled. It did not help.

Have googled, no answer yet.

---

### Post by mooreted on 2010-06-19
Tried to compile from source:

checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.2.0                         gthread-2.0 >= 2.2.0                         gobject-2.0 >= 2.2.0... Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package gthread-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gthread-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gthread-2.0' found Package gobject-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gobject-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gobject-2.0' found
configure: error: Library requirements (glib-2.0 >= 2.2.0                         gthread-2.0 >= 2.2.0                         gobject-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I am not running the dependency treadmill.

---

### Post by mooreted on 2010-06-20
Oh well, I'll just use Grabit on xp in my vm. It must have something to do with the AMD quad core processor because it works fine on my other computer with a Celeron processor.

---

