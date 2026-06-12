---
title: "Chrome, FF, banshee will not start (after update)"
date: 2011-10-14
forum: General Help
---

### Post by Biopyro on 2011-10-14
They all show in the taskbar as if they're initialising, but at the point they usually load and show up onscreen, they just dissapear.


```
[3:3:1923837030:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
 
[6:6:1923904685:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
 
[10:10:1923978125:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
 
Inconsistency detected by ld.so: dl-open.c: 597: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!
```

That's the output of starting chrome in terminal.


I am also having a problem with the taskbar and top bar, I do not know how to add icons or applications to them. You can no longer move shortcuts on them either?

Thanks for your help.

---

### Post by Mguel on 2011-10-21
Having similar problema... after a system crash, rebooted and haven't been able to make chromium work again. deleted profile, reinstall it, complete removal, reinstall, updated to latest ppa build, no luck...

it shows, even after profile delete I get to the screen where I select which search engine chromium will use, but after it force closes

```
agm@hpdm1:~$ chromium-browser 
Gtk-Message: Failed to load module "canberra-gtk-module"
[2333:2343:1101545855:ERROR:gl_implementation.cc(91)] Could not initialize GL.
[2333:2343:1101546049:ERROR:gl_surface_linux.cc(66)] InitializeRequestedGLBindings failed.
[2333:2343:1101546117:ERROR:gpu_info_collector_linux.cc(216)] gfx::GLContext::InitializeOneOff() failed
[3:3:1101875275:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
Inconsistency detected by ld.so: dl-open.c: 597: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

```

---

### Post by Biopyro on 2011-11-09
I wound up having to simply format and start afresh. I could find no solution, presumably after 4 updates I just needed a clean slate.

---

