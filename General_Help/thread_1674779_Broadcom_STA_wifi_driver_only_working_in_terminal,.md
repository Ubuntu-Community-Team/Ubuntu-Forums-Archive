---
title: "Broadcom STA wifi driver only working in terminal, whats wrong?"
date: 2011-01-24
forum: General Help
---

### Post by beancheese on 2011-01-24
Hi,

I just bought a Lenovo B560, everything working except the Broadcom 4727 wireless (only in terminal it works) any ideas?

---

### Post by TeoBigusGeekus on 2011-01-24
Try [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by gordintoronto on 2011-01-24
What do you mean, "only in terminal it works"? Do you have a wireless connection or not?

---

### Post by beancheese on 2011-01-24
Should have been more specific, the STA driver only lets me do a iwlist scan, network manager doesn't show any networks.
could you tell me how ndiswrapper work, would appriciate it :)

---

### Post by beancheese on 2011-01-24
when i try installing ndisgtk all it says is this

```
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

thanks alot, seems like I'm going to use proper b43 or b43legacy driver :)

---

