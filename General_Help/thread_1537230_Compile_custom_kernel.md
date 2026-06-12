---
title: "Compile custom kernel"
date: 2010-07-23
forum: General Help
---

### Post by dioxip on 2010-07-23
Hello !

The past hours I've been working on compiling my own kernel.
I have been following this guide: 
[http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html]("http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html")

Everything went well until, I should generate the ramdisk.
I can't get this command working. 
```
mkinitramfs -o initrd.img-2.6.34.1 2.6.34.1
```

I get this error:
```
sudo mkinitramfs -o initrd.img-2.6.34.1 vmlinuz-2.6.34.1
cp: missing destination file operand after `/tmp/tmp.SwwnoFlZEK/sbin/'
Try `cp --help' for more information.
------------------
Error has occured!

```

So my question is. What went wrong?


//dioxip

---

### Post by dioxip on 2010-07-23
bump

---

