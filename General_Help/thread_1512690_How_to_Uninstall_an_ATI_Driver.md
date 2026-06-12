---
title: "How to Uninstall an ATI Driver"
date: 2010-06-18
forum: General Help
---

### Post by boaty on 2010-06-18
Hey everyone,

Earlier this morning, I stupidly installed this ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)) driver in an attempt to rid myself of the AMD Unsupported Hardware watermark.

This lead to me having two sets of drivers.  The one installed from the Properties -> Hardware Drivers and this one.

Basically, right now I uninstalled the Hardware Drivers one in an attempt to find the .run driver.  However, I can't.

Does anyone know how I can get rid of that driver, so I can then go back to using the one Hardware Drivers installs?

Thanks in Advance.

---

### Post by boaty on 2010-06-18
I've been researching this for the last 4 hours.  Can anyone help me?

Edit:
Finally, got this.
I reinstalled with the .run file, then ran "sudo apt-get -f install", then I reinstalled with Hardware Drivers and it's all good.

Very odd, but whatever.

---

