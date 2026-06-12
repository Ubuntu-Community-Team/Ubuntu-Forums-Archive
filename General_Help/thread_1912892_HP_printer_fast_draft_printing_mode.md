---
title: "HP printer fast draft printing mode"
date: 2012-01-21
forum: General Help
---

### Post by samuelm on 2012-01-21
The HP driver for Windows supports a "fast draft" mode for HP printers. However, when I try to configure my HP printer on my Kubuntu machine, CUPS doesn't show me this mode in the selection of modes. Is it because the driver doesn't support it? Or is there some sort of "hidden" way to enable it?

---

### Post by sanderd17 on 2012-01-21
What driver are you using?

There are different drivers available for HP printers.

For my printer, the CUPS+gutenprint driver gives the most options (including low-quality printing).

---

### Post by samuelm on 2012-01-21
I tried both the "hpcups" and the "hpijs" and neither one allows me to do fast-draft printing.

---

### Post by sanderd17 on 2012-01-21
> **samuelm said:**
> I tried both the "hpcups" and the "hpijs" and neither one allows me to do fast-draft printing.

Those are both HP drivers for CUPS. Can you check if you have the package [cups-driver-gutenprint]("http://packages.ubuntu.com/oneiric/cups-driver-gutenprint") installed?

That should give better drivers.

---

### Post by samuelm on 2012-01-21
Yes, I do. However, there is no CUPS+gutenprint driver option for my printer, an HP PSC 1401.

---

### Post by sanderd17 on 2012-01-21
> **samuelm said:**
> Yes, I do. However, there is no CUPS+gutenprint driver option for my printer, an HP PSC 1401.

That probably means Gutenprint doesn't support your printer.

I can't help you much further.

BTW, most things I know about cups, I got from the Arch wiki: [https://wiki.archlinux.org/index.php/CUPS](https://wiki.archlinux.org/index.php/CUPS)

---

