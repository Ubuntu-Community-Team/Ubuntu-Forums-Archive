---
title: "dm-crypt encrypted root, /home, swap. Can I unlock these 3 with one password?"
date: 2011-07-06
forum: General Help
---

### Post by Sycron on 2011-07-06
So, I set up a manual disk encryption using dm-crypt/LUKS. I have the root encrypted, along with the swap space and /home (but not the boot partition).
> /boot unencryted
/home encrypted
/ encrypted
swap encrypted

All these partitions have the same password. Is it possible to unlock them at the same time without entering the same password three times at boot?

---

### Post by Sycron on 2011-07-06
Problem solved. Reinstalled the system following [http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system]("http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system").

---

