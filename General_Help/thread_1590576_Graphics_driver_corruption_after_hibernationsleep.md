---
title: "Graphics driver corruption after hibernation/sleep?"
date: 2010-10-08
forum: General Help
---

### Post by MackieChan on 2010-10-08
After getting [sleep/hibernation to work]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/522998/comments/30"), every time I hibernate or sleep and then restore, 3D graphics do not seem to work.

For example, I'll have an opengl program up or webgl demo up in chrome, before hibernation and it will work fine.  After waking up, if I try to do the webgl demo, chrome freezes, and trying the opengl program will just show whatever was at that point of the screen (eg if it was hovering over the desktop, the opengl program shows the desktop instead of the actual 3D content).

The ATI Catalyst Control Center won't even open after waking up (it will before hibernation).

Additionally, while I can use the fglrxinfo command before sleep (output below), after sleep when I try to use it, it seems to run forever (not freeze, I can still type characters but it doesn't do anything).

System Specs:  ATI 5770, I7-930, USB 3.0 (which is why I had a problem getting the system to sleep in the first place).

output of fglrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series
OpenGL version string: 4.0.10237 Compatibility Profile Context
```

I'm running K/Ubuntu 10.10, but I know it does the exact same thing on 10.04, which uses different graphics drivers, I believe.

If you need any more info, I'll provide it, but I'm not really sure what else would help

---

