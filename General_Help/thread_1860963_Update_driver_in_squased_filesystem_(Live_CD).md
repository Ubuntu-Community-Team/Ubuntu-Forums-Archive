---
title: "Update driver in squased filesystem (Live CD)"
date: 2011-10-15
forum: General Help
---

### Post by kfleten on 2011-10-15
Hi

I have a Live CD with a thin client software built on top of a 9.04 squashed filesystem. Now, I need to make this thin client software work with a particular graphics card. I have got a lot of help from the guide at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization).

Unfortunately, I have not found any recent 9.04 binaries for the properitary ATI fglrx driver, so I have to run the installer file from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

When working with the installer in the unsquashed filesystem, the install fails due to missig dkms. I believe this is because the kernel is not actually running when working on the unsquashed filesystem.

If I boot the Live CD, I actually can install, and dkms gives no errors. The problem is only that I can not -naturally- save changes in a live cd. I have created deb-files inside the live session, and copied them to a USB stick, and then tried to install them later on the unsquashed filesystem, but that did not help.

Is it possible to use dd or something similar to copy the entire running live cd down to a USB stick ? Is there any other files than the deb's that should be copied out from the Live session ?

---

