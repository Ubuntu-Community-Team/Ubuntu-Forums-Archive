---
title: "ATI Radeon x1650, Compiz, and Emerald"
date: 2009-09-16
forum: General Help
---

### Post by joeyyyy on 2009-09-16
I've been trying to get this to work for the past week or so and I've had no success.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 
Results in black screen before login.

RadeonHD also results in white screen after login.

Restricted drivers with acceleration enabled gets a white screen after login.

Reload windows decorators on the Compiz Fusion Icon either gets a white screen or makes the windows lock in place.

compiz --replace, emerald --replace, no effect.

I've just reinstalled Ubuntu and am open to any suggestions.

Running Ubuntu 8.04 with 2gb ram, 2.3 ghz amd, and an ATI Radeon x1650 512mb AGP card.

---

### Post by P4man on 2009-09-17
You can not use the binary ATi drivers for that card; Im afraid its no longer supported by AMD:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

You're stuck with the opensource "ati" driver, Im not sure if that supports compiz.

edit: oops, didnt notice you were still running ubuntu 8.04. There should be binary drivers for that I think.

---

### Post by joeyyyy on 2009-09-17
> **P4man said:**
> You can not use the binary ATi drivers for that card; Im afraid its no longer supported by AMD:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

You're stuck with the opensource "ati" driver, Im not sure if that supports compiz.

edit: oops, didnt notice you were still running ubuntu 8.04. There should be binary drivers for that I think.

There are indeed binary drivers for ati, but if you read my original post, I've already stated that it doesn't work for me.

As for the opensource drviers, I'll try it out and edit my original post with results.

---

