---
title: "untitled window"
date: 2009-10-30
forum: General Help
---

### Post by James Dee on 2009-10-30
Hello,

When I start abaqus cae one untitled window appeared on the screen (see attachment) and I can not close that window.

The program is started from terminal with:
```
XLIB_SKIP_ARGB_VISUALS=1 abaqus_dir/abaqus cae
```

Also on error appeared:
```
X Error: code 154 major 144 minor 5: GLXBadContext.

Warning: Your system needs to be reconfigured to allow OpenGL
rendering to a pixmap or Pbuffer; otherwise, you will not be
able to print or use the probe function in Abaqus/CAE.
```
But I don't know how to allow OpenGL rendering.

Is this error or starting program without desktop effects conected with the untitled window?

Thnx...

---

### Post by James Dee on 2009-11-01
bump

---

### Post by James Dee on 2009-11-03
fglrxinfo gave this output:
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 2.1.8543 Release
```

Are these informations helpful?
Which infos I can provide to gave you clearer picture what is happening on the system?

---

### Post by James Dee on 2009-12-14
Problem solved....

Set visual effects to None.

---

