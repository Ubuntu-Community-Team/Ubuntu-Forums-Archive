---
title: "nVidia Dapper"
date: 2006-05-06
forum: General Help
---

### Post by bobpaul on 2006-05-06
I've been running Dapper for a while, but just did an update to Dapper Beta (it's been about 2 months since my last update I think)

nVidia driver no longer works. When I put **Driver "nvidia"** in my xorg.conf I get *(EE) Failed to load module "nvidia" (module does not exist, 0)*

I've tried uninstalling and reinstalling the nvidia module that's in aptitude. Anyone have any ideas? For the time **Driver "nv"** works, but then I loose twinview, which is a drag.

---

### Post by Jason_25 on 2006-05-06
You need the restricted modules for your kernel version.

---

### Post by tseliot on 2006-05-06
uninstall the nvidia driver from aptitude

Then try my script which will install the driver automatically (with Method 2):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

