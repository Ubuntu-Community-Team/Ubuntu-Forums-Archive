---
title: "dpkg-reconfigure, initrd and modules"
date: 2006-03-04
forum: General Help
---

### Post by rysiek on 2006-03-04
hi there

I've been using Kubuntu for some time now and wanted to do some tweaks on my box - at last I found some time. I thought it would be nice to have the console at 1024x768x16bpp, so I added vga=791 to my kernel's arguments. And then - ooops! when booting I get insmod complaining about not being able to load vesafb.ko kernel module ("no such file or directory").
Well, thought I, it's a simple thingy - just edit /etc/mkinitramfs/modules and it should be AOK. Edited (added "vesafb" line), checked that the MODULES var is set to "most" in /etc/mkinitramfs/initramfs.conf and... dpkg-reconfigure linux-image-$(uname -r). And rebooted.

...and got the same error! :-? 

Done some testing and everytime - the same error. As if dpkg-reconfigure linux-image-$(uname -r) would IGNORE the modules file. But it doesn't ignore initramfs.conf file (tested with the RESUME var). WTF?

I'm starting to run out of ideas. Any help?

Cheers
Mike

---

### Post by rysiek on 2006-03-04
Heh, got it - it's bug #17331 in bugzilla ([http://bugzilla.ubuntu.com/show_bug.cgi?id=17331)](http://bugzilla.ubuntu.com/show_bug.cgi?id=17331)).
Should've looked there first, sorry for that.

Cheers
Mike

---

