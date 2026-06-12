---
title: "Brother DCP 7030 driver does not show in CUPS admin."
date: 2009-12-05
forum: General Help
---

### Post by nmcb on 2009-12-05
This will probably be a newbie question; I have installed the Brother DCP-7030 printer drivers from the Brother site:

  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030)

I installed the LPR driver first and the CUPS wrapper second, but the driver does not show up in my CUPS admin page. Am I missing something?

As additional information; I'm running ubuntu 9.10 (32-bit), my DCP-7030 is connected via USB to a Apple Timecapsule. My Laptop is on the wireless network provided by the capsule. CUPS admin does find my DCP-7030 via DNS-SD.

If I'm unable to install the correct driver I'll be more then happy if somebody points me to a compatible driver in the ubuntu 9.10 default printer driver database. The existing DCP-7010 / 7020 / 7025 drivers seem not to work with my setup (infinite form feeds, oh joy!)

All comments are welcome, thanks in advance,
nmcb

---

### Post by nmcb on 2009-12-05
Ubuntu was missing the dir where the cups wrapper installs the ppd file.

> sudo mkdir /usr/share/cups/model

After this, reinstall the cups wrapper and the driver will show up.

---

