---
title: "xgl + xserver frozen"
date: 2006-06-19
forum: General Help
---

### Post by analyzer on 2006-06-19
Hello together

I try to install xgl with this howto:
[http://www.ubuntuforums.org/showthread.php?t=127090](http://www.ubuntuforums.org/showthread.php?t=127090)

All run fine until start xglcompmgr 
```
LD_LIBRARY_PATH=/opt/mesalibs DISPLAY=:1 konsole
```
Open a new shell, but there are some errors.
```
xlib: extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
```

In the new shell: 
```
/opt/mesalibs# /opt/fdo/bin/glxcompmgr shadow wobbly
```

The background will get black. The xserver frozen.

Do you have some ideas?

I use an ATI Readon 9800 Pro IceQ graphic-card and KDE (Kubuntu Drapper)

Thanks.

---

### Post by analyzer on 2006-06-20
It was a small mistake in the filename (libGL.so.1.2). But there is an other problem.

```
/opt/fdo/bin/glxcompmgr gconf cube expose fade rotate shadow wobbly zoom
```

Follow error:
```
glxcompmgr: GLX_MESA_render_texture is missing
  	glxcompmgr: Failed to manage screen: 0
 	glxcompmgr: No managable screens found on display :1.0
```

EDIT: I use Mesa mesa 6.5-1

---

