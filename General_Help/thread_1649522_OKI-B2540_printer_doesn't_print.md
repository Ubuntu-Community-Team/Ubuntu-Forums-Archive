---
title: "OKI-B2540 printer doesn't print"
date: 2010-12-20
forum: General Help
---

### Post by NCLI on 2010-12-20
There is a driver for the OKI-B2520, and it is automatically selected when the printer is connected. From looking at various websites, it seems like the B2500, B2520, and B2540 all work perfectly fine with the OKI-B2520 driver, so I let it install that. Everything went smoothly, the printer shows up as available, and I can queue jobs without any problems, and they disappear after a few seconds.

However, nothing actually comes out. There is no error message on the printer display, or from Ubuntu.

What could be wrong? The printer worked perfectly fine under Windows.

[This]("http://pastebin.com/S6ifZAup") is the output from /var/log/cups/error.log.

---

### Post by joelkat on 2010-12-20
is the printer supported by linux?

---

### Post by NCLI on 2010-12-20
> **joelkat said:**
> is the printer supported by linux?

It shows up just fine, and acts like it's working, so yes.

---

### Post by kubug on 2011-01-30
Looking at openprinting.org it shows your printer as supported:

[http://www.openprinting.org/printer/Oki/Oki-B2540_MFP](http://www.openprinting.org/printer/Oki/Oki-B2540_MFP)

Have you tried their supplied PPD? Sometimes the PPD that comes with ubuntu didn't work for me:

[http://www.openprinting.org/ppd-o-matic.php?driver=Postscript&printer=Oki-B2540_MFP&show=0](http://www.openprinting.org/ppd-o-matic.php?driver=Postscript&printer=Oki-B2540_MFP&show=0)

---

