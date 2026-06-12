---
title: "are my configs being ignored?"
date: 2005-02-15
forum: General Help
---

### Post by chbenito on 2005-02-15
I've got a slightly unusual monitor, it's native resolution is 1280x768. I have edited the XF86Config-4 to reflect this, specifying the only acceptable resolution as 1280x768. Unfortunately, the x-server seems to be trying to display as 1280x960.

I tried using x.org from hoary, but it totally ignored the xorg.conf and never found a usable resolution before giving up and aborting.

Are there other configs besides those in /etc/X11?

Thanks.
Christian

---

### Post by streetbmx on 2005-02-27
did you make sure XF86Config-4 was renamed to xorg.conf?

---

