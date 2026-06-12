---
title: "how to create a /dev/fb0 device"
date: 2009-07-22
forum: General Help
---

### Post by shredder12 on 2009-07-22
I am using an application that uses the frame buffer devices but when I run it I get this error.
```
Open /dev/fb0 : No such file or directory
```

As the problem says this is because there is no such file or directory..
so I think probably creating one will solve the problem..
So, can anyone suggest a way to create this frame buffer device..

---

### Post by ajgreeny on 2009-07-22
> **shredder12 said:**
> I am using an application that uses the frame buffer devices but when I run it I get this error.
```
Open /dev/fb0 : No such file or directory
```As the problem says this is because there is no such file or directory..
so I think probably creating one will solve the problem..
So, can anyone suggest a way to create this frame buffer device..
I have never used it but I think you need ```
sudo mknod /dev/fb0
``` but you may need some options in there as well.  Have a look at man mknod for more info.

---

### Post by sisco311 on 2009-07-22
Just set a framebuffer resolution in GRUB and reboot.
[https://wiki.ubuntu.com/FrameBuffer#Setting different framebuffer resolutions in GRUB]("https://wiki.ubuntu.com/FrameBuffer#Setting different framebuffer resolutions in GRUB")

---

### Post by shredder12 on 2009-07-22
ya now I am able to use both of the applications..
view image as  well as the pdf..
but I am having some trouble with the resolution..
actually the problem is only with the alignment of the ubuntu logo at the time of boot..
its not at the center..
so I was wondering if there is a way to align it..

---

### Post by hellocatfood on 2011-01-15
I'm having a bit of trouble with this myself. I've tried executing "sudo mknod /dev/fb0" but got "mknod: missing operand after `/dev/fb0'"

---

