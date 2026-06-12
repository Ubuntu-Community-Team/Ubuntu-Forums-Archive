---
title: "Is it possible to use older graphics drivers with 11.04?"
date: 2011-06-13
forum: General Help
---

### Post by oopsie on 2011-06-13
For me, Ubuntu 11.04 can only use "software rasterizer" with Open GL. I think this is possibly because I have to disable kernel mode-setting on my PC and the new drivers with 11.04 need KMS to work. Though that's just my guess.

In Ubuntu 10.04 hardware accelerated OpenGL works fine with KMS off.

So does anybody know how I can use those older drivers in 11.04?

OR

Does anybody know how to make Ubuntu 11.04's drivers work with KMS disabled?

---

### Post by idoitprone on 2011-06-13
The real question is which kernel version the graphic drivers works with.

What your graphics card and is the driver open source or proprietary.
If its an open source driver from intel or nouveau project, then you need kms. 

If not, then disable kms and hope the driver works on newer kernel.

---

