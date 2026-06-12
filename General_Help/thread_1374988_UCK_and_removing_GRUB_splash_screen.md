---
title: "UCK and removing GRUB splash screen"
date: 2010-01-07
forum: General Help
---

### Post by HuckleSmothered on 2010-01-07
I'm using UCK to remaster a LiveCD of Ubuntu 9.10.

One big thing I'm really wanting to do is have it skip the GRUB2 menu and just boot right into the LiveCD, no options for installing, no options for memory test, etc. Just straight boot.

However, changing the GRUB2 settings in the UCK chroot environment has no effect that I can see. It always gives the same menu and the same 30 second timeout (no matter the time I tell it to use).

When I update grub in the chroot environment, it doesn't find anything (memtest if I don't remove the 30-memtest grub script first) but that's it. Yet it still gives the menu. I've also tried removing the os-prober script without any results.

Any suggestions?

---

