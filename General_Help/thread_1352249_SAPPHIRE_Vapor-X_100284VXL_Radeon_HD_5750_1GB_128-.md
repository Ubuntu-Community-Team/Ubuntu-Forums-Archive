---
title: "SAPPHIRE Vapor-X 100284VXL Radeon HD 5750 1GB 128-bit GDDR5 PCI Express 2.0 x16 HDCP"
date: 2009-12-11
forum: General Help
---

### Post by kevinwmiller on 2009-12-11
Is this supported by Ubuntu 9.10?

---

### Post by lukeiamyourfather on 2009-12-21
Ubuntu 9.10 comes with ATI Catalyst 9.10 in the repositories (no relation in version number, just a coincidence). That driver supports Radeon HD 5800 series but not 5700 series. There is a newer version of the driver available for download from ATI but you'd have to manually install the driver for it to work. Cheers!

---

### Post by Burnout on 2010-01-15
Hello,

I've got the card.

When you install the standard repo Karmic fglrx drivers, a logo "not supported hardware AMD" appears in the right bottom corner of the screen.
When you install the newest 9.12 binary drivers, the logo dissapears and everything seems to work.

BUT, the driver/card isn't stable. Xorg crashes on random actions. :( Sometimes it's only the videocard which crashes, sometimes the whole pc freezes. 

Has somebody the same problem? What about the other 5700 cards? Is there a fix?

---

### Post by Burnout on 2010-01-23
This problem is solved. Sapphire told me to upgrade my VBIOS. The new VBIOS adjust the powerplay function in 2D mode. :)

---

