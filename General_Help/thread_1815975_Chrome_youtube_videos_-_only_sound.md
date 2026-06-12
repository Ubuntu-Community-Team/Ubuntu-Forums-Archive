---
title: "Chrome youtube videos - only sound"
date: 2011-08-01
forum: General Help
---

### Post by Kojot89 on 2011-08-01
I am using Google Chrome 12.0.742.124 and Chromium 12.0.742.112,
Both web browsers have the same bug. When I play youtube videos sometimes the player is not loaded properly. I hear sound but I don't see video and player navigation buttons. I need to refresh page several times to get youtube player loaded.

How to solve this problem?

---

### Post by Jouke S on 2011-08-01
Try upgrading the ubuntu-restricted-extras packages via package manager or terminal. This package also includes Flash, which youtube uses to display videos.

---

### Post by Kojot89 on 2011-08-01
> **Jouke S said:**
> Try upgrading the ubuntu-restricted-extras packages via package manager or terminal. This package also includes Flash, which youtube uses to display videos.

I installed the newest ubuntu-restricted-extras (version 43), but this issue still occurs.

When I type:
```
chrome://plugins
```
I can see that nothing changes in the Flash section. It uses:
```
Shockwave Flash 10.3 r181
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

```

---

### Post by turtle153 on 2011-08-01
I too have this problem and I have **Version: 11.0.1** which is the Beta

---

### Post by baughd2 on 2012-03-12
I found the solution on another site.

[http://www.google.com/support/forum/p/Chrome/thread?tid=29f2bd4b11373d4f&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=29f2bd4b11373d4f&hl=en)

Basically, it has something to do with a hardware accelerator.
Just right click on a working youtube video screem, then hit settings, click the display icon (A picture of a monitor) then un-check "Enable hardware acceleration"
Worked for me, hope this helps

---

