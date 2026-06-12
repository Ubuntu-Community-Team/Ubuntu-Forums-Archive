---
title: "How to install kernel loop module?"
date: 2009-08-03
forum: General Help
---

### Post by Tom Chaudoir on 2009-08-03
Overview:
This command has always worked in the past.
```
sudo modprobe loop
```

Since upgrading to Jaunty it returns:
> FATAL: Module loop not found.

How do I install the loop module in Jaunty?

Background:
I'm following this article to mount an iso image:
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html")

Thanks in advance,
Tom

---

### Post by nomnex on 2009-08-29
Exact same question here

```
mtpc03@mtpc03-laptop:~$ sudo mount -o loop ~/Software/clonezilla-live-20090812-jaunty.iso /Media/ISO_image/clonezilla-live-20090812-jaunty.iso
mount: mount point /Media/ISO_image/clonezilla-live-20090812-jaunty.iso does not exist
mtpc03@mtpc03-laptop:~$ sudo modprobe loop
FATAL: Module loop not found.
```Thanks

On another thread [http://ubuntuforums.org/showthread.php?t=1156789](http://ubuntuforums.org/showthread.php?t=1156789)
> You don't need to "modprobe loop" in 9.04, the loopback driver is compiled into the kernel, not as a module.

If so, why can't I pass the command?

---

### Post by gsocker on 2009-08-29
The reason you are getting the error message:
```
mount: mount point /Media/ISO_image/clonezilla-live-20090812-jaunty.iso does not exist
```
is that the directory you want to use as the mount point does not exist; you need create it with "mkdir" before running mount. It does not automatically appear.
Try this:
```

sudo mkdir /media/clonezilla
sudo mount -o loop ~/Software/clonezilla-live-20090812-jaunty.iso /media/clonezilla

```

---

### Post by nomnex on 2009-08-29
Edit: Thanks, problem solved

---

