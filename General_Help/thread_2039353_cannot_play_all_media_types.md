---
title: "cannot play all media types"
date: 2012-08-08
forum: General Help
---

### Post by Unguidedone on 2012-08-08
the icons that dont have a picture dont play unless i use vlc player.

[IMG]http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/Workspace1_003.png[/IMG]

---

### Post by mc4man on 2012-08-08
likely a current gstreamer bad plugin bug
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

To test to see if affected or as a hack around if affected
On a 64 bit install
```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```

On a 32 bit install
```
sudo mv /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```

If doing the above fixes playback in gstreamer apps like totem then if desired a more proper fix is to rebuild the plugin with a patch to fix this (waiting on Debian/Ubuntu will prove to be a long one

I show one way to do so here - 
[http://ubuntuforums.org/showpost.php?p=12118375&postcount=6](http://ubuntuforums.org/showpost.php?p=12118375&postcount=6)

---

