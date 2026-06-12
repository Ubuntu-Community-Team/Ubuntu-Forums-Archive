---
title: "[ask] What is difference between..."
date: 2011-01-07
forum: General Help
---

### Post by Ryuuji on 2011-01-07
Hello, this is my first thread.
What is difference between linux-image-xxxx, linux-headers-xxxx, linux-headers-xxxx-generic, linux-image-generic, and linux-headers-generic?

When i upgrade new kernel, i always install linux-image-xxxx, linux-headers-xxxx, and linux-headers-xxxx-generic. but my friend said he just install linux-headers-xxxx-generic and it works.

sorry for my bad english. i'm asian

---

### Post by JKyleOKC on 2011-01-07
The file that your friend installs has the other required files listed as dependencies, so they are automatically installed without him having to specify them. This is one of the major benefits of the package manager systems used here (Synaptic, aptitude, apt-get, and possibly a few others, all of which use the "dpkg" back-end where the magic happens).

---

### Post by MaxIBoy on 2011-01-07
The linux-image and linux-headers are dummies, so you could technically remove them (DON'T) if you kept the -generic packages. They are there for the convenience of the package managers, and you don't have to worry about it.

It doesn't really matter, but if your curious, linux-image is the actual kernel, whereas linux-headers are necessary if you want to install any kernel modules (like hardware drivers.)

---

### Post by Ryuuji on 2011-01-07
Ah, i understand now :D
Thanks a lot both of you :D

---

