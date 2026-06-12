---
title: "Trying to compile OGMRip"
date: 2006-06-19
forum: General Help
---

### Post by reclusivemonkey on 2006-06-19
I am trying to compile OGMRip. I've insalled build-essential, and all the necessary packages via synaptic. After ./configure, I get;

```

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for OGMRIP_CFLAGS...
checking for OGMRIP_LIBS...
configure: error: Package requirements (glib-2.0 >= 2.6.0 gobject-2.0 >= 2.6.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the OGMRIP_CFLAGS and OGMRIP_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

As far as I can tell, I have glib-2.0 and gobject-2.0 installed. I am currently using AcidRip, but it often fails to work, and when I leave it overnight it seems to completely shutdown my machine of its own accord (no, I do not have shutdown ticked in the options). OGMRip was my preferred choice on my old Slackware desktop and it worked flawlessly. Its a shame this isn't in the repositories. Howcome its not in there???

---

