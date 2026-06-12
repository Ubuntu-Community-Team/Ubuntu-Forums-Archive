---
title: "Screen saying out of range"
date: 2011-03-26
forum: General Help
---

### Post by Spyderkid on 2011-03-26
when i load ubuntu the screen says 'out of range' after the loading screen, I fixed this by changing the refresh rate or something by holding down <Ctrl><Alt><=><-> however now i just get a black load up screen without even the ubuntu word and loading dots. Even though after that all is normal.

I have an awfull built in graphics card

---

### Post by Spyderkid on 2011-03-27
anyone?

---

### Post by PCNetSpec on 2011-03-27
Try adding something like **vga=771** as a kernel boot parameter. (or **nomodeset**)

See here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

640x480 vga=769
800x600 vga=771
1024x768 vga=773
1280x1024 vga=775
1600x1200 vga=796

The above are all 256 Colour modes, for a more comprehensive table, see here:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

Or tell us a bit more about your hardware (specially graphics hardware).

---

### Post by Spyderkid on 2011-03-27
I have 1440x900 resolution?

---

### Post by bkratz on 2011-03-27
It is also in the wikipedia link under "Linux video mode numbers"

---

### Post by PCNetSpec on 2011-03-27
Doesn't mater what your monitor can handle... for now, just set vga=771, because pretty much all graphics cards and monitors can handle that... if it works, you can take it from there.

---

### Post by Spyderkid on 2011-03-27
I haven't yet done the vga=771 but the load up screen is back to the text boot up with the purple background and stuff just not the fancy graphics...

shall i still do vga=771

---

