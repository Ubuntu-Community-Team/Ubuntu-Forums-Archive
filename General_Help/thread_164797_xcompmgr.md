---
title: "xcompmgr"
date: 2006-04-23
forum: General Help
---

### Post by Fysidiko on 2006-04-23
When I run xcompmgr I get a series of errors:
error 9 request 155 minor 4 serial 785
error 9 request 155 minor 4 serial 795
error 9 request 155 minor 4 serial 805
error 9 request 155 minor 4 serial 815
error 9 request 155 minor 4 serial 825
error 9 request 155 minor 4 serial 835
error 9 request 155 minor 4 serial 845
error 9 request 155 minor 4 serial 7389
error 4 request 54 minor 0 serial 7764

Any ideas what's wrong?

Thanks.

---

### Post by Kethinov on 2006-04-23
These errors are normal with xcompmgr because it is not yet stable. However, it should still work and do what it is supposed to do. If it is doing what it is supposed to do, then don't worry about it. If it's not working at all, you need to check to make sure composite is enabled in your xorg.conf, and that you have a sufficiently fast video card with the correct drivers installed.

---

### Post by Fysidiko on 2006-04-24
It's not running - when I run xcompmgr everything just vanishes and I have to close the terminal window (or ctrl-C) to get it back. I have composite enabled in my xorg.conf, and I'm running an nvidia 7800 GT with correct drivers - glxgears gives about 15000 FPS - so I'd hope I have the graphical 'horsepower' to run a bit of translucency...

---

### Post by Kethinov on 2006-04-24
Did you compile it yourself or install it from some dpkg somewhere? I generally find compiling xcompmgr myself results in a more stable result.

---

### Post by Fysidiko on 2006-04-24
Got it via apt-get - I'll have a try at compiling it and post the results.

---

