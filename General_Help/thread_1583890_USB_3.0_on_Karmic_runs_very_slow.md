---
title: "USB 3.0 on Karmic runs very slow"
date: 2010-09-28
forum: General Help
---

### Post by ehagood on 2010-09-28
I have a Dell server with Dual 2.26GHz Xeon Processors with 8 GB of RAM. I installed a PCI Express USB 3.0 card and upgraded my Ubuntu to Karmic 9.10 (which is supposed to have USB 3.0 support). I run a back-up of the system through the USB 3.0 to a USB 3.0 HD and not only is the transfer slow (about 55 MB/s) it is slowing the system down.
 
The HD is encrypted with dmcrypt, using LUKS. Between the decrypt and the rsync I run to copy over the back-up files... it is taking up around 110% of the processors (200%) being max.
 
Does anyone have any idea why the USB 3.0 would be running so slow and why it would slow the server down?
 
Thanks,
Eddie

---

