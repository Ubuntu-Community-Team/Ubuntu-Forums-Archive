---
title: "Brightness Controls not working."
date: 2011-04-29
forum: General Help
---

### Post by xadz on 2011-04-29
Hey there,

I just installed Ubuntu 11.04 on to my Samsung N150 Netbook and everything seems to working just great apart from that my brightness controls aren't working.  They bring up the brightness meter where the FN brightness buttons on my PC will make it go up and down although they have no effect on the actual screen's brightness.

Also, is there any way to get rid of that bar on the left?  In an attempt to save space it's actually reduced it and now I have to use the horizantal scroll bar on web pages I browse, very annoying.

Any help would be very much appreciated as it's currently very dark.  Thank-you!

---

### Post by dino99 on 2011-04-29
brightness:

Try this.

sudo gedit /etc/default/grub

Change the line GRUB_CMDLINE_LINUX="" into GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

Restart your linux

removing unity:

from synaptic: remove/purge ubuntu-desktop & unity

---

### Post by xadz on 2011-04-29
> **dino99 said:**
> brightness:

Try this.

sudo gedit /etc/default/grub

Change the line GRUB_CMDLINE_LINUX="" into GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

Restart your linux

removing unity:

from synaptic: remove/purge ubuntu-desktop & unity
Thanks!  That's rid of Unity but my brightness controls still don't effect the actual screen brightness.

---

