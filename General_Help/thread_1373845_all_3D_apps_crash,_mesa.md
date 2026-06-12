---
title: "all 3D apps crash, mesa"
date: 2010-01-06
forum: General Help
---

### Post by barna on 2010-01-06
Hi,

On my notebook (Toshiba Satellite, Radeon) all of the 3D apps I have tried (wings3d, k3d, blender, etc) crash, right after startup. dmesg sais after starting k3d, for example:

```

[ 5970.338716] k3d-bin[2418]: segfault at 6102677 ip 060aeb43 sp bf93e420 error 7 in radeon_dri.so[605e000+24f000]

```

radeon_dri.so is part of the package libgl1-mesa-dri, and the mesa 7.6.0 release notes (here: [http://mesa3d.sourceforge.net/relnotes-7.6.html](http://mesa3d.sourceforge.net/relnotes-7.6.html)) say:

> 
Mesa 7.6 is a new development release. People who are concerned with stability and reliability should stick with a previous release or wait for Mesa 7.6.1


Ubuntu clearly is not concerned with stability, since it uses in karmic mesa-7.6.0. This is only one example. In one of the earlier releases they used the 'cutting-edge, new-technology, etc etc' KDE4, which was in such an early stage, that I could not even set up shortcut keys, and many things just crashed (making a lot of users complain).

Who knows, wether there will there a mesa upgrade in karmic?

---

