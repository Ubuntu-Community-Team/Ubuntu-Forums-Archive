---
title: "Please tell me I did this right. (Installation)"
date: 2009-07-22
forum: General Help
---

### Post by -spy on 2009-07-22
I just installed Ubuntu, full install on a 30gb partition, that worked fine I suppose, BUT my boot screen changed, instead of saying "Windows 7" Then  "Vista"(I deleted this partition before installing) below, it loads up a GRUB screen with a about 4 Ubuntu startup options, then below that 2 "Windows/Longhorn" options. Why did the boot screen change completely?

Then, I kinda freaked thinking I deleted my main windows partition (I didn't) but when booting up the second Windows/Longhorn" option it went into some kind of :C Disk recovery screen, checking all this stuff (never seen that before). It works fine though.

My question is, was that SUPPOSED to happen? The boot screen change, the :C Disk check? Will it :C Disk check everytime now?

---

### Post by bacil on 2009-07-22
because you replaced windows boot loader with grub. there is nothing wrong with it and grub recognised your two previous boot options as longhorn correctly thats code name for win7 and vista (same codebase) i belive

---

### Post by -spy on 2009-07-22
Can I get the Windows boot loader back? I don't guess it's that big of a deal but..

And what about that :C Disk check? Will that happen again?

---

### Post by Tyke91 on 2009-07-22
that C: diskcheck shouldn't happen again.

why would you want windows bootloader back? Grub is better and windows can't boot a linux box :)

grub can be manually edited on the fly (passing commands to the kernel for example enforcing=0 for selinux enabled boxes), and it even supports themes! :)
[http://farm3.static.flickr.com/2058/2111749660_64a9125986_o.png](http://farm3.static.flickr.com/2058/2111749660_64a9125986_o.png)

---

### Post by ibutho on 2009-07-22
You shouldn't worry about the disk check. That sometimes happens when something has changed in the partition table or you have resized partitions. As for restoring the Windows bootloader, you can use the methods described [here]("http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/") or use the [SuperGrubDisk]("http://www.supergrubdisk.org").

---

