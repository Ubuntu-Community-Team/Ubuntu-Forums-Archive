---
title: "How to get Windows to read a Ubuntu USB drive?"
date: 2011-06-06
forum: General Help
---

### Post by william_ia on 2011-06-06
Hi All,

We are using Ubuntu 10.04 LTS with VMware View Open Client software to connect to a server with a Windows XP image on it. I have found that VMware is missing the capablities to pass the USB drive to the windows image. Does anyone know the specifics of how to work around this issue?
I have seen similar problems addressed here, but have not found an exact match where the USB redirect is missing.

01. Is this a mount issue where the USB drives are not properly mounted to be passed to the Windows image?
02. Or are we missing a driver or other software that would make the USB ports visible in the Windows Image?

I have seen where some have tried working with /etc/fstab folder. What i get when is do a fdisk -l is:

Device                Boot      Start            End           Blocks            ID      System
/dev/sda1              *           1             18663     149903360         83       Linux
/dev/sda2                         18663        19458         6384641          5       Extended
/dev/sda5                         18663        19458         6384640         82      Linux swap / Solaris

I am looking for a lot of help here as we are fast approaching a deadline to get this deployed!!

Thanks in advance!!

---

