---
title: "Help needed desperatly, re startup config"
date: 2005-01-27
forum: General Help
---

### Post by RobDollar on 2005-01-27
In brief: I need the command line that boots the live cd into 800x600.



I have an old-ish 14inch monitor, and it can't handle over 800X600.  After the boot splash (live cd), ubuntu goes to a higher resolution than my monitor can handle, and therefore I can't use it.

Does anyone know what command line I should set at the boot splash? I've tried various settings but I can't get it to work.

Any help greatly appreciated, and sorry if this has already been answered elsewhere, I have searched everywhere for info.

-Rob.

---

### Post by az on 2005-01-27
sudo dpkg-reconfigure xserver-xfree86

---

### Post by misGnomer on 2005-01-27
These are the 800x600 boot codes for *Knoppix* that I've come across. I still haven't seen a list of boot parameters for Ubuntu-live, but since many of the "[Knoppix cheat codes](http://www.knoppix.net/wiki/Cheat_Codes)" seem to work, you could try one of these:


e.g.  "*linux vga=788*"
or     "*linux fb800x600*"


# Use fixed framebuffer graphics
# fb800x600

# VESA framebuffer console @ 800x600x64k
# vga=788

# VESA framebuffer console @ 800x600x32k
# vga=787

# VESA framebuffer console @ 800x600x256
# vga=771


These two seem to be specific to X (once it gets started):

# "xres=800x600"  or
# "screen=800x600"


I hope these won't smoke your grand old SVGA tube...  :-\"

---

