---
title: "Permission denied for executing files on the external storage"
date: 2010-01-24
forum: General Help
---

### Post by hgadre on 2010-01-24
Hello,

I have a dual boot Dell Studio laptop with Windows (VISTA) and Ubuntu (9.0.4) installed on it. I have recently installed Ubuntu to make it  a dual boot. Before that I was using LiveUSB Ubuntu  image for six months (without any problems).

During the installation of Ubuntu, I created a Linux partition of 2GB for Ubuntu installation (assuming that it was running successfully on my 2GB USB drive). All of my other work (e.g. documents/programming projects etc.) are stored on the Windows partition (which is loaded during the boot time automatically). The problem is that I get a "permission denied" error while running any executable file on the Windows partition. But if I copy the same executable on the Linux partition, everything works perfect. Am I missing something here?

I have verified that the executable have necessary execute permissions.

---

### Post by hgadre on 2010-01-24
Hello,

Can you please provide any feedback on this problem?

---

### Post by ppirilla on 2010-01-24
I assume that the vista partition is formatted as NTFS?

I try to avoid microsoft partition types whenever possible, but it seems likely that NTFS is just not capable of giving a file executable permission.

---

### Post by hgadre on 2010-02-04
I am not sure how that can be a problem because everything was working fine when I was using Ubuntu LiveUSB. Should I try to shrink the Windows partition and create a new Linux partition? Will that solve the problem?

---

### Post by gmargo on 2010-02-05
> **hgadre said:**
> I am not sure how that can be a problem because everything was working fine when I was using Ubuntu LiveUSB.

If it was working with the LiveUSB, trying booting from the LiveUSB again, and inspect the options it used to mount the NTFS partition (/etc/fstab file).  Then compare the options used in the Linux partition.

---

