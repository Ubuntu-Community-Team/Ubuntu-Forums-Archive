---
title: "uninstalling a printer driver"
date: 2009-11-12
forum: General Help
---

### Post by semperlinux on 2009-11-12
Hi Forum,

I've been trying to get a printer driver to install on my Ubuntu 9.10 Siemens Scenic desktop.

The driver is for a Brother QL500 label printer - written by Brother and released about 2 years ago under the GPL.  As Ubuntu 9.10 is considerably 'younger', the driver has obviously not been tested with Ubuntu 9.10.
I've been in touch with Brother about this and they are looking into it.

The driver doesn't install correctly because of a conflict.
 
My current problem is that I'd like to uninstall the driver but the following occurs.

Synaptic says it can't uninstall the driver - uninstall runs but does not complete and returns the following......
"Error: sub process installed post-installation script returned error exit status 127"

The following is some terminal o/p when running DPKG commands................

dpkg -l lists the driver as present but the status (in the LH column) is "iF"  - it should be "ii" when correctly loaded.

dpkg -P --force-all [driver name] reports that it cannot uninstall the driver as it is not present !!

"Forcing" the uninstall doesn't work. Until now I've just been reformatting the root partition and re-installing Ubuntu.

Anyone any ideas on how I can get rid of this driver ?

Thanks for your time
Semperlinux.

---

