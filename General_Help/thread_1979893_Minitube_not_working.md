---
title: "Minitube not working"
date: 2012-05-14
forum: General Help
---

### Post by alwindoss on 2012-05-14
Minitube the default version in Ubuntu 12.04 does not work as expected, Wehn I play a sng it stops in the first few minutes and then it moves to the next song and I can't see the video too.

---

### Post by mc4man on 2012-05-14
There are several things plaguing minitube on 12.04. It crashes sometimes when switching vids, (known bug), switches before vid is done, & fails to properly decode many video's.

The decoding issue can be worked around by either switching the backend to vlc, (requires some work to do) or by removing a specific gstreamer bad plugin

For 64 bit install
```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```

32 bit install

```
sudo mv /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```

Decoding bug
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)

---

### Post by Bucic on 2012-05-18
I did the trick with vlc backend. Minitube still crashes constantly.

---

### Post by Bucic on 2012-05-29
It seems to be working fine now after I updated it to 1.7
[Minitube 1.7 Released (PPA) ~ Web Upd8: Ubuntu / Linux blog](http://www.webupd8.org/2012/01/minitube-17-released-ppa.html)

---

### Post by Bucic on 2012-05-30
> **mc4man said:**
> 
The decoding issue can be worked around by either switching the backend to vlc, (requires some work to do) or by removing a specific gstreamer bad plugin

For 64 bit install
```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```

32 bit install

```
sudo mv /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```

Decoding bug
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)
How to undo these actions?

EDIT:
```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so
```
_probably_ did the trick.

---

