---
title: "Stuck in Low Graphics Mode - any advice?"
date: 2009-12-12
forum: General Help
---

### Post by DrawnToScale on 2009-12-12
Did a system upgrade in 9.10 last night, and this morning I'm stuck in low graphics mode. Here's what I see that I try to boot up:

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized
(EE) fglrx(0): FB pci_device_map_range error!
(EE) fglrx(0): Failed to map FB memory
(EE) fglrx(0): Failed to disable interrupts.  Errorcode -9
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9

Any suggestions would be most appreciated!

---

### Post by dcstar on 2009-12-12
> **DrawnToScale said:**
> Did a system upgrade in 9.10 last night, and this morning I'm stuck in low graphics mode. Here's what I see that I try to boot up:

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized
(EE) fglrx(0): FB pci_device_map_range error!
(EE) fglrx(0): Failed to map FB memory
(EE) fglrx(0): Failed to disable interrupts.  Errorcode -9
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9

Any suggestions would be most appreciated!

Your ATI video drivers did not install correctly, try:

System-Administration-Hardware Drivers

---

### Post by DrawnToScale on 2009-12-13
> **dcstar said:**
> Your ATI video drivers did not install correctly, try:

System-Administration-Hardware Drivers

Thanks.  I did what you suggested and saw that the "ATI/AMD proprietary FGLRX graphics driver" was not activated.  I selected it and clicked "Activate".  Looked like something downloaded.  I then re-booted, but the problem remains, and this driver is still listed as not activated.

Any other ideas....?

---

### Post by DrawnToScale on 2009-12-13
Perhaps this will help give some clues.  When I last did a system software upgrade, I got these error messages:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic_2.6.31-16.52_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic_2.6.31-16.52_i386.deb) 
  404  Not Found 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic-pae_2.6.31-16.52_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic-pae_2.6.31-16.52_i386.deb) 
  404  Not Found 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16_2.6.31-16.52_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16_2.6.31-16.52_all.deb) 
  404  Not Found 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16-generic_2.6.31-16.52_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16-generic_2.6.31-16.52_i386.deb) 
  404  Not Found

Again - any help would be most appreciated in restoring me to full graphics mode!

---

### Post by DrawnToScale on 2009-12-14
> **DrawnToScale said:**
> Perhaps this will help give some clues.  When I last did a system software upgrade, I got these error messages:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic_2.6.31-16.52_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic_2.6.31-16.52_i386.deb) 
  404  Not Found 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic-pae_2.6.31-16.52_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic-pae_2.6.31-16.52_i386.deb) 
  404  Not Found 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16_2.6.31-16.52_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16_2.6.31-16.52_all.deb) 
  404  Not Found 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16-generic_2.6.31-16.52_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16-generic_2.6.31-16.52_i386.deb) 
  404  Not Found

Again - any help would be most appreciated in restoring me to full graphics mode!

I went to Admin/Software Updates and checked for additional updates.  More were downloaded and installed, but I'm still stuck in low-graphics mode.   Do I need to re-install the OS, or is there something less drastic I can do????

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
I'd work to get the proprietary drivers working. If that still doesn't fix it you may have to edit your xorg.conf.

---

