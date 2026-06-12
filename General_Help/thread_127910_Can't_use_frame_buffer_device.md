---
title: "Can't use frame buffer device"
date: 2006-02-10
forum: General Help
---

### Post by publicv on 2006-02-10
Hi,
    I'm trying to use framebuffer devices, I've followed the
instructions at:

[http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html)

and it seems as if I've got it working (when I boot with the VGA=ASK
parameter I can choose my desired resolution and the console changes
appropriatly), and I also have frame buffer devices in /dev (/dev/fb0
was there at the beginning and I have created another one with ``mknod
/dev/fb1 c 29 32´´).

However, when I try to check that the fb device is really working with
``fbset -i´´ i get:
open /dev/fb0: No such device

running it as superuser also gives the same result. However, this file
exists:

ls /dev/fb*
/dev/fb0  /dev/fb1

Any idea what's wrong? How can I get the frame buffere device working?

Thanks in advance,
publicv.

---

### Post by dcstar on 2006-02-10
[QUOTE=publicv]Hi,
    I'm trying to use framebuffer devices, I've followed the
instructions at:
......
Any idea what's wrong? How can I get the frame buffere device working?

Thanks in advance,
publicv.[/QUOTE]
To my (limited) understanding, FrameBuffer only works with the VESA driver, are you using that in your xorg.conf?

---

