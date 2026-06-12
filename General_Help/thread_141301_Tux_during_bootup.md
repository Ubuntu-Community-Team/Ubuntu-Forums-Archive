---
title: "Tux during bootup?"
date: 2006-03-08
forum: General Help
---

### Post by munchies on 2006-03-08
Is there anyway that I could change the way Ubuntu boots up..   I'd like to be able to see what is going on.. IE.. no GUI.. and preferably I'd like to see Tux.. like Gentoo.

---

### Post by evilgold on 2006-03-08
easy, just remove "splash" from your menu.lst options...

like ```
title		Ubuntu, kernel 2.6.15-17-k7
root		(hd0,0)
kernel		/vmlinuz-2.6.15-17-k7 root=/dev/mapper/vol0-main ro quiet **splash**
initrd		/initrd.img-2.6.15-17-k7
savedefault
boot

```

change to
```
title		Ubuntu, kernel 2.6.15-17-k7
root		(hd0,0)
kernel		/vmlinuz-2.6.15-17-k7 root=/dev/mapper/vol0-main ro quiet
initrd		/initrd.img-2.6.15-17-k7
savedefault
boot

```

---

### Post by keeb on 2006-03-08
Is there a way to change the splash image?

---

### Post by evilgold on 2006-03-08
okay after consulting with the experts (aka my gentoo using friends)

I figured out how to get tux to show up, you need to compile a new kernel to do so, and i did this with gentoo so i'm not sure if the normal ubuntu source will have the feature (but it should). Anyways look for these options under menuconfig or xconfig

```

DEVICE DRIVERS--->
Graphics support  --->
[*] Support for frame buffer devices
   [INDENT][/INDENT] [*]   VESA VGA graphics support
    Console display driver support  --->
        [*]   Video mode selection support
        <*> Framebuffer Console support
     Logo Configuration --->
         [*]Bootup Logo
         [*]   Standard 224-color Linux logo 

```> [QUOTE][QUOTE][/QUOTE][/QUOTE]

---

