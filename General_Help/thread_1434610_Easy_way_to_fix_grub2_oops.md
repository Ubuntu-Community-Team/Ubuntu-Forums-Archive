---
title: "Easy way to fix grub2 oops"
date: 2010-03-20
forum: General Help
---

### Post by NHclimber on 2010-03-20
Just recently, I modified the menu text code in grub2 (private copy, not in the distribution).  I was stripping it down to just the menu entries without the title, box, help text and moving the menu entries to where I wanted them relative to the graphic background.  After I rebooted, I was locked out of my machine completely.  No grub console, no rescue mode, nada.  Oops.

But this is not about that. It's about giving kudos to three great resources that bailed me out of a tight jam:

[LIST]
[*]A fantastic section on troubleshooting in this post [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
[*]SuperGrubDisk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) - I ended up not using this, but they had a link to...
[*]UNetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))
[/LIST]

UNetbootin offers a quick and easy way to put nearly any distribution or boot-time tool onto a USB stick. On my Windows laptop, I downloaded and ran their Windows app.  All from within their app, I selected what I wanted (Ubuntu 9.10 Live) - which downloads the iso from their site - wrote out the iso to the USB stick and made the USB stick bootable.  In 20 minutes (downloading took the lion's share), I was back on my primary machine fixing my oops!  Thanks!

PS - They do offer a Linux app but I didn't try that.

---

