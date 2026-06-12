---
title: "x11vnc as service- Shift issues"
date: 2010-08-25
forum: General Help
---

### Post by leezer3 on 2010-08-25
Marginally feel like bashing my head against a wall :p
I've quite happily had x11vnc running as a service on a headless box for a while now. This week I upgraded the system to 10.04, and have run into an issue whereby the shift key isn't being handled properly. This is on launchpad ( [https://bugs.launchpad.net/ubuntu/+source/x11vnc/+bug/551147](https://bugs.launchpad.net/ubuntu/+source/x11vnc/+bug/551147) ), but the listed workaround of adding -xkb to the launch paramaters isn't working.

I'm launching x11vnc via init.d , using the /usr/local/bin method.
My x11vnc.sh currently looks like this after listed workaround:
```
#!/bin/sh
/usr/bin/x11vnc -inetd -o /var/log/x11vnc.log -display :0 \ -auth /root/xauth -many -bg -xkb
```

xev shows the correct keystrokes being sent, so this looks to me like this is definitely x11vnc being the pain here.
I've also tried -nomodtweak both in concert with -xkb and alone, but this doesn't do anything.

Anyone see what I'm missing?

---

### Post by krunge on 2010-08-25
Post all of /var/log/x11vnc.log here.

---

### Post by leezer3 on 2010-08-25
```
25/08/2010 14:01:24 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 2686
25/08/2010 14:01:24 Using X display :0
25/08/2010 14:01:24 rootwin: 0x101 reswin: 0x4400001 dpy: 0x9796648
25/08/2010 14:01:24 
25/08/2010 14:01:24 ------------------ USEFUL INFORMATION ------------------
25/08/2010 14:01:24 X DAMAGE available on display, using it for polling hints.
25/08/2010 14:01:24   To disable this behavior use: '-noxdamage'
25/08/2010 14:01:24 
25/08/2010 14:01:24   Most compositing window managers like 'compiz' or 'beryl'
25/08/2010 14:01:24   cause X DAMAGE to fail, and so you may not see any screen
25/08/2010 14:01:24   updates via VNC.  Either disable 'compiz' (recommended) or
25/08/2010 14:01:24   supply the x11vnc '-noxdamage' command line option.
25/08/2010 14:01:24 
25/08/2010 14:01:24 Wireframing: -wireframe mode is in effect for window moves.
25/08/2010 14:01:24   If this yields undesired behavior (poor response, painting
25/08/2010 14:01:24   errors, etc) it may be disabled:
25/08/2010 14:01:24    - use '-nowf' to disable wireframing completely.
25/08/2010 14:01:24    - use '-nowcr' to disable the Copy Rectangle after the
25/08/2010 14:01:24      moved window is released in the new position.
25/08/2010 14:01:24   Also see the -help entry for tuning parameters.
25/08/2010 14:01:24   You can press 3 Alt_L's (Left "Alt" key) in a row to 
25/08/2010 14:01:24   repaint the screen, also see the -fixscreen option for
25/08/2010 14:01:24   periodic repaints.
25/08/2010 14:01:24 
25/08/2010 14:01:24 XFIXES available on display, resetting cursor mode
25/08/2010 14:01:24   to: '-cursor most'.
25/08/2010 14:01:24   to disable this behavior use: '-cursor arrow'
25/08/2010 14:01:24   or '-noxfixes'.
25/08/2010 14:01:24 using XFIXES for cursor drawing.
25/08/2010 14:01:24 GrabServer control via XTEST.
25/08/2010 14:01:24 
25/08/2010 14:01:24 Scroll Detection: -scrollcopyrect mode is in effect to
25/08/2010 14:01:24   use RECORD extension to try to detect scrolling windows
25/08/2010 14:01:24   (induced by either user keystroke or mouse input).
25/08/2010 14:01:24   If this yields undesired behavior (poor response, painting
25/08/2010 14:01:24   errors, etc) it may be disabled via: '-noscr'
25/08/2010 14:01:24   Also see the -help entry for tuning parameters.
25/08/2010 14:01:24   You can press 3 Alt_L's (Left "Alt" key) in a row to 
25/08/2010 14:01:24   repaint the screen, also see the -fixscreen option for
25/08/2010 14:01:24   periodic repaints.
25/08/2010 14:01:24 X FBPM extension not supported.
25/08/2010 14:01:24 X display is capable of DPMS.
25/08/2010 14:01:24 --------------------------------------------------------
25/08/2010 14:01:24 
25/08/2010 14:01:24 Default visual ID: 0x21
25/08/2010 14:01:24 Read initial data from X display into framebuffer.
25/08/2010 14:01:24 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
25/08/2010 14:01:24 
25/08/2010 14:01:24 X display :0.0 is 32bpp depth=24 true color
25/08/2010 14:01:24 
25/08/2010 14:01:24 setsockopt: Socket operation on non-socket
25/08/2010 14:01:24 
25/08/2010 14:01:24 Xinerama is present and active (e.g. multi-head).
25/08/2010 14:01:24 fb read rate: 373 MB/sec
25/08/2010 14:01:24 fast read: reset wait  ms to: 10
25/08/2010 14:01:24 fast read: reset defer ms to: 10
25/08/2010 14:01:24 The X server says there are 10 mouse buttons.
25/08/2010 14:01:24 screen setup finished.

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching

25/08/2010 14:01:24   other clients:
25/08/2010 14:01:24 setsockopt failed: Socket operation on non-socket
caught signal: 2
25/08/2010 14:01:29 deleted 32 tile_row polling images.
```

Complete log :)
Can't see any xkb complaints or messages in there though.

---

### Post by krunge on 2010-08-25
> ```

25/08/2010 14:01:24   other clients:
25/08/2010 14:01:24 setsockopt failed: Socket operation on non-socket
caught signal: 2
25/08/2010 14:01:29 deleted 32 tile_row polling images.
```

You have specified '-inetd' but you are not using inetd. (I think you said you are simply running it from a startup script, is that what you meant by 'init.d' /usr/local/bin method?)

So remove the '-inetd' from the command line. OTOH if you are using inetd, show the details of that configuration.

Also, for temporary testing, add '-dk' to the x11vnc cmdline to enable keyboard debugging so we can tell that -xkb is enabled.  Also add '-v'.

---

### Post by leezer3 on 2010-08-26
Arrgh, I seem to have wider problems. Tried the log again this morning, and it hadn't changed ](*,)

This led me to another copy of x11vnc being spawned by GDM, which I removed. This killed my VNC access entirely.

A reboot, and the init.d copy now loads, but complains about port 5900 being in use. I've shifted it to 5901 on a temp basis, and it's working, but I'm now trying to find what's spawning on 5900.

Thoughts?
Tempted to try a complete rebuild, but this install is coming on for 5 years old, and I can do without that hastle :(

---

### Post by igorp1024 on 2010-09-22
Did you try to use "-sloppy_keys"?

---

