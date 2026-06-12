---
title: "Changed Console Resolution, Virtual Console gone"
date: 2011-04-05
forum: General Help
---

### Post by Archie Moses on 2011-04-05
Console was in 640x480,

Made the following edits to /etc/default/grub, in red.

GRUB_CMDLINE_LINUX_DEFAULT="quiet [COLOR=Red]nomodeset[/COLOR]"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=[COLOR=Red]1024x768 (Alternatively 1366x768 monitors native resolution)[/COLOR]
[COLOR=Red]GRUB_GFXPAYLOAD_LINUX=keep[/COLOR]

Any of the resolutions (640x480, 1024x768, 1366x768) will not bring the console back.  These are the only system changes, coming off a fresh install.

Any thoughts on the other two lines?  Ubuntu Newb.

Thanks!

---

### Post by Archie Moses on 2011-04-05
[COLOR=Red]GRUB_GFXPAYLOAD_LINUX=keep
[COLOR=Black]
The offending line.  But now can't change console res.[/COLOR]
[/COLOR]

---

