---
title: "gphoto2 2.4.5/2.4.8 with canon eos 500d - lucid"
date: 2010-04-24
forum: General Help
---

### Post by roasttoe on 2010-04-24
Hi all!

I'm having problems using my Canon EOS 500D with gphoto2 - the app appears to work fine when launched using:

```
paul@thermal:~/Documents$ gphoto2 --capture-tethered --hook-script test-hook.sh
test-hook.sh: INIT
test-hook.sh: START                                                            
Waiting for events from camera. Press Ctrl-C to abort.
```

However, the camera will become unresponsive. When pressing the trigger, it will not respond but say "Busy".  After a few presses gphoto will terminate with the following error:

```
*** Error ***              
Canon EOS Get Changes failed: 2ff
test-hook.sh: STOP

```

I am using the most up-to-date version of gphoto2 in the Ubuntu repos, but according to the developer's website it is slightly behind. However, it is using the latest libgphoto2, which supports my camera. I have very little knowledge about compiling from source so have not tried this approach.

```

This version of gphoto2 is using the following software versions and options:
gphoto2         2.4.5          gcc, popt(m), exif, cdk, aa, jpeg, readline
libgphoto2      2.4.8          gcc, ltdl, EXIF
libgphoto2_port 0.8.0          gcc, ltdl, USB, serial without locking

```

Any suggestions would be most helpful.  I suspect that Gnome auto-mounting my camera may cause a problem but cannot be sure.

Many thanks!
P.

---

### Post by Yury Samsonov on 2011-06-20
Hi! I had same problems with my 450D.

Yes, you're right, auto-mounting can cause problems - you can see something like "Can't lock camera", sorry, I can't check actual message as autorun is disabled on my PC. Try to unmount your camera with popup menu (right click on camera icon).

If your camera is "busy" when you run gphoto with --capture-tethered, try to take a picture with --capture-image param. It worked for me.

---

