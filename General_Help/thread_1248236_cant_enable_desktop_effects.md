---
title: "cant enable desktop effects"
date: 2009-08-23
forum: General Help
---

### Post by bmck on 2009-08-23
i just installed ubuntu 9.04 and i went to ati.com and got the latest drivers for my card its a radeon hd 2600. i cant change screen res i just cant enable desktop effects

# glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

# compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: xterm 
no xterm found, exiting

---

### Post by P4man on 2009-08-24
Looks like the drivers werent installed.
rather then getting them from ATI though, get them from the repositories. Go system > adminstration > hardware drivers.

Select the recommended drivers from there.

---

