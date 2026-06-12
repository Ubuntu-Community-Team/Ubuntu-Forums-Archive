---
title: "Cant install 10.10 on new computer"
date: 2010-10-23
forum: General Help
---

### Post by Oddi on 2010-10-23
Hi all

I just put together a new computer, started to install win7 and then tried to install Ubuntu.

Ubuntu (The installer) tells me that I don't have at least 2.6 GB available drive space...

I have a 640GB SATA 3.0 HD and the only thing on it is win7. On previous versions of Ubuntu this was never an problem. Ubuntu always helped me with the partition.

I have tried both the 64 and 32 bit versions of Ubuntu 10.10 and get the same result.  

Why doesn't Ubuntu help me with the partition ?

Thanks in advance
Oddi

---

### Post by Oddi on 2010-10-23
I really need help with this...

Wubi doesn't work either. When rebooting from wubi it says it cant find the image and wants me to run chkdsk /r (in windows), I have tried that and nothing helps. 

Does Ubuntu/Linux not support the SATA 3.0 ??

---

### Post by Oddi on 2010-10-23
Found a solution.

Ubuntu needs AHCI enabled for the Sata-3 controller in order to correctly identify the disks on it

This blog provided the solution:

[solution]("http://loo.no/2010/09/29/installing-ubuntu-10-10-on-a-sata-3-disk")

---

