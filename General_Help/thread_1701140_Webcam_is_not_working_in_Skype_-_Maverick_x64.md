---
title: "Webcam is not working in Skype - Maverick x64"
date: 2011-03-06
forum: General Help
---

### Post by Rushyang on 2011-03-06
Previously I had installed 32 bit version..and my webcam wasn't detecting in 32 bit version.. 

I found solution that installing cheese webcam booth would also install the standard webcam 2.0 drivers and skype was detecting web cam through following command line..

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &


BUT, now I'm on 64 bit version and and skype is not detecting my webcam.. 

Any solution?

---

