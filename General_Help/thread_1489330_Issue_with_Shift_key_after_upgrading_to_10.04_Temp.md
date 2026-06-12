---
title: "Issue with Shift key after upgrading to 10.04 Temporary Fix"
date: 2010-05-21
forum: General Help
---

### Post by Hoochster on 2010-05-21
I just updated to 10.04 and all the sudden my shift key would no longer work.  I fixed it and am sharing what I found here, but background of how I run my system first.  I am running Xubuntu via VMWare-Server and I connect to it via X11VNC.  After some research I came to find that it was an issue with X11VNC, if I used regular VNCServer it worked fine.  So that gave me something to google, and sure enough it is a known issue.  But there was a workaround:

[http://www.bramschoenmakers.nl/en/node/714](http://www.bramschoenmakers.nl/en/node/714)

To sum it up, when you run x11vnc just pass the -xkb flag.  Simple command ie.

```
x11vnc -display :0 -xkb
``` 

And that fixed my issue till they fixe x11vnc.  Just wanted to share for anyone that runs into the issue.

---

### Post by krunge on 2010-05-22
Could you run x11vnc without "-xkb" and add the options "-nopw -dk" and then paste or attach the full output here?

Your problem may be fixed in x11vnc 0.9.10 and the above output should have enough info to show if it is fixed or not.

---

