---
title: "help me please !!!"
date: 2006-06-26
forum: General Help
---

### Post by nimes on 2006-06-26
(sorry my english)
Hi,
i update compiz packages to quinn4 today. also update libgl-mesa, libdrm etc.

but starting error xgl after update.

glxinfo | grep rendering
direct rendering : NO

how to fix???

---

### Post by KaridaSerious on 2006-06-26
Direct rendering does not work when running Xgl, but it does on Xorg.

Direct rendering implies hardware acceleration, but not the other way round. Direct rendering is a bit faster than indirect rendering, but indirect rendering is not as bad as it sounds.

Direct rendering is active if running glxinfo|grep direct on top of Xorg (not Xgl!) shows you "Yes". On top of Xgl this will always show you "No". Unfortunately, for Xorg having direct rendering is a synonym for having accelerated graphics, and it is more difficult to detect whether hardware accleration is available than it is to detect direct rendering.

[http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl)

---

### Post by nimes on 2006-06-26
i'm working xorg
this error after update

---

