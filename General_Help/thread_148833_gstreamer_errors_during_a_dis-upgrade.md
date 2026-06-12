---
title: "gstreamer errors during a dis-upgrade"
date: 2006-03-22
forum: General Help
---

### Post by kybishop on 2006-03-22
So i added a few repositories from the source-o-matic, then did a dist upgrade, to my surprise, there were something like 54 new upgrades, most of them gstreamer something.12

During the dist-upgrade, error messages starting popping up
```

Setting up gstreamer0.8-flac (0.8.12-0unofficialubuntu1) ...
libvisual WARNING: no progname: visual_plugin_get_list(): Failed to add the /usr/lib/libvisual/actor directory to the plugin registry
libvisual WARNING: no progname: visual_plugin_get_list(): Failed to add the /usr/lib/libvisual/input directory to the plugin registry
libvisual WARNING: no progname: visual_plugin_get_list(): Failed to add the /usr/lib/libvisual/morph directory to the plugin registry
libvisual WARNING: no progname: visual_plugin_get_list(): Failed to add the /usr/lib/libvisual/transform directory to the plugin registry
```

Its basically repeating those errors for a bunch of gstreamers

its still in the midst of the dist-upgrade, so no way to tell if anythings broken yet, but regardless, i was wondering what the errors mean, and if there's a way to fix them (or if it's worth fixing)

---

