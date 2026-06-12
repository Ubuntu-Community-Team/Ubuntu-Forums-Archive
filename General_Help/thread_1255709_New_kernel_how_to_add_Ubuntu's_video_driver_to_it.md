---
title: "New kernel how to add Ubuntu's video driver to it?"
date: 2009-09-01
forum: General Help
---

### Post by rcayea on 2009-09-01
Right now I am using the ubuntu video driver. You know the one that you get when you scan hardware drivers in the system->Administration section. 

So I use that but then I went into Ubuntu's kernel ppa and installed kernel 2.6.30-02063005-generic. Point is, it is a fairly new kernel update. 

Each time I boot into that kernel, my computer doesn't realize that I am using the ubuntu-provided-video driver. I always end up having to boot into a low-level mode and when I do get to the desktop I can't activate the video hardware driver.

Any thoughts?

Thanks,
Randy

---

### Post by alphacrucis2 on 2009-09-01
> **rcayea said:**
> Right now I am using the ubuntu video driver. You know the one that you get when you scan hardware drivers in the system->Administration section. 

So I use that but then I went into Ubuntu's kernel ppa and installed kernel 2.6.30-02063005-generic. Point is, it is a fairly new kernel update. 

Each time I boot into that kernel, my computer doesn't realize that I am using the ubuntu-provided-video driver. I always end up having to boot into a low-level mode and when I do get to the desktop I can't activate the video hardware driver.

Any thoughts?

Thanks,
Randy

What graphics card do you have?

---

### Post by falconindy on 2009-09-01
I've tried a handful of kernel compiling methods, and the one that I've stuck with is [this one](http://blog.avirtualhome.com/2009/04/29/how-to-compile-a-kernel-for-ubuntu-jaunty/) in part because it doesn't screw with your graphics drivers. I'm honestly not sure what the technical difference is, but this method has worked for me reliably about a half dozen times now.

---

### Post by rcayea on 2009-09-01
> **alphacrucis2 said:**
> What graphics card do you have?


I have an Nvidia 9500.

---

### Post by rcayea on 2009-09-01
> **falconindy said:**
> I've tried a handful of kernel compiling methods, and the one that I've stuck with is [this one](http://blog.avirtualhome.com/2009/04/29/how-to-compile-a-kernel-for-ubuntu-jaunty/) in part because it doesn't screw with your graphics drivers. I'm honestly not sure what the technical difference is, but this method has worked for me reliably about a half dozen times now.

I really like this link. At first it appears to be way more than just video drivers but is seems like it would be fun to try and learn from it. 

Thanks.

---

