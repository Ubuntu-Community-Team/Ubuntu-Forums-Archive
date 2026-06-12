---
title: "USB &amp; UI question/help"
date: 2011-12-10
forum: General Help
---

### Post by MonthOLDpickle on 2011-12-10
How much space does it take on a USB to install a bootable linux with no persistence? I tried to use a 2 GB..with the program and maxed out persistence. But it errored and I am still trying to make my UBS readable..which I think may be fixed soon..


So how much space? When I slide the slider it did the full stick (like 1900mb..I should have questioned it).

Also how can I installed a netbook GUI with my USB linux boot drive and also keep desktop - just switch at upon log in.

---

### Post by dabl on 2011-12-10
Depending on what you mean by "a bootable Linux", the answer could be as small as 175 MB - that's about the size of my Parted Magic installation.  Other "Live CD" distros might range up to 800 MB.

As it looks like you are deep into self-education on the topic, may I recommend [[COLOR="SeaGreen"]**this**[/COLOR]](http://manual.aptosid.com/en/hd-install-opts-en.htm#fromiso) guidance?

And [[COLOR="SeaGreen"]**here**[/COLOR]](http://kubuntuforums.net/forums/index.php?topic=3107512.0) is more.

---

### Post by WasMeHere on 2011-12-10
Hi MonthOLDpickle,

If you make the boot USB stick with Unetbootin, you can make it without persistence. Afterwards you can fill the empty space on the stick with a casper-rw file according to tips on the internet (on the root directory of the stick).
[[COLOR="RoyalBlue"]_http://forums.linuxmint.com/viewtopic.php?f=42&t=14209&start=15_[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=42&t=14209&start=15")

You tell the boot-system look for the casper-rw-file by entering ***persistent*** at the end of a line in the file ***syslinux.cfg***
```
append initrd=/ubninit file=/cdrom/preseed/mint.seed boot=casper quiet splash persistent --
```

Have fun finding out :-)
Olle

*Edit: There is a max file size in FAT32: The file must be less than 4GB, which might be a problem on a big stick.*

---

