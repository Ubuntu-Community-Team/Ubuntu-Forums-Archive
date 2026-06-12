---
title: "How to set up one, non-persisent, netboot pxe image for many?"
date: 2009-07-19
forum: General Help
---

### Post by lumix on 2009-07-19
How can I do this?

I'd like for ***ALL*** changes but a user's data to be non-persisent and to apply to the local machine only.  Even the slightest change to the boot image (background, icon arrangement, *anything*) would not only be an administrative affair, but really only possible by re-imaging. Something  like having all client machines booting from one Ubuntu CD, using the "no changes to your system" option.

Yes, I've read the diskless howto, but it only briefly mentions that maybe I should consider mounting things as tmpfs.  Well an Ubuntu installation is a big place and I don't know *what* to mount as tmpfs.  To me , it would seem easier to start with that CD image, and make /home non-perishable.

---

### Post by t4thfavor on 2009-07-19
Your looking for kiosk mode...

Something like this thread is mentioning:
[http://ubuntuforums.org/archive/index.php/t-338980.html](http://ubuntuforums.org/archive/index.php/t-338980.html)

---

### Post by hugmenot on 2009-07-19
Well, I think you&#8217;re looking for this:
[http://ubuntuforums.org/showthread.php?t=1112209&highlight=pxelinux.cfg](http://ubuntuforums.org/showthread.php?t=1112209&highlight=pxelinux.cfg)

---

