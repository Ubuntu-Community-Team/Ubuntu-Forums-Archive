---
title: "ATI Open Source drivers: No hardware acceleration"
date: 2011-03-13
forum: General Help
---

### Post by pteri498 on 2011-03-13
I have an ATI Mobility Radeon HD 5000 series (I believe 5470, but I forget).

I installed the open source ATI drivers using instructions at [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver").

Wonderfully, this gives me triple monitor support (LVDS, VGA, and HDMI at the same time), which the proprietary drivers couldn't do for me.

But now I don't have 3D support (and XBMC crawls horribly as a result.) glxinfo shows me I have software rendering:

```
$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

```

I'm not finding anything on Google or the forums finding out how to fix this. Does anyone have any ideas?

Thanks.

---

### Post by pteri498 on 2011-03-13
Fixed!

I added the xorg-edgers PPA and ran the Update Manager to update my drivers, and now things are going fine with 3D acceleration.

```

$ sudo apt-add-repository ppa:xorg-edgers/ppa

```

GLXInfo:

```

$ glxinfo | grep OpenGL
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (CEDAR 68E0) 20090101  TCL DRI2
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

```

And glxgears runs great, too (though I didn't test beforehand so I don't have any comparisons to make).

---

