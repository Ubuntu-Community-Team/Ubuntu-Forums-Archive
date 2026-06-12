---
title: "Can't start X in anything but root account."
date: 2006-06-14
forum: General Help
---

### Post by mootchell on 2006-06-14
I've been trying to get xgl/compiz to work for quite a while now. Finally this afternoon, it worked, I played a video ... and it crashed.

I know how to fix that problem (it's been asked all over), and in fact i had already gotten rid of the zoom problem in compiz when this happened.

**Upon restarting, x will not load.** It is telling me something repeatedly about the directory "**/dev/wacom**." Something to the effect of that it will not open.

Also, "**/usr/share/X11/font/misc**" and it's refcount being 2 when it should be one. I cannot paste the exact output here as I don't think you can copy from the pure terminal and paste once x (root account) starts up.

So.. **I can't start X** as my regular (customized) user name on this computer. **I can only start X as root** after I do a quick SU in the pure terminal I am forced into after trying to start X as my regular user.

What is a refcount, anyway?
Anyone think they can help?

---

### Post by mootchell on 2006-06-14
Someone apparently has the same problem I do, however, no one answered them...

[http://paste.ubuntu-nl.org/15160](http://paste.ubuntu-nl.org/15160)

For those who don't want to click.. This is what it is (and exactly what's happening to me!!!):

```

Error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
```

Anyone?

---

### Post by caserio on 2006-06-14
Hi,

Maybe you shouldn't be using that crappy xgl/compiz thing...

Try this:
edit you /etc/X11/xorg.conf then comment (#) the lines concerning the wacom driver (Section "InputDevice" and Section "ServerLayout").

---

