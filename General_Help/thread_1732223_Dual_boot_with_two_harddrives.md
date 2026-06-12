---
title: "Dual boot with two harddrives"
date: 2011-04-18
forum: General Help
---

### Post by cmb991 on 2011-04-18
Maybe someone can help me out.  Is there anyway to dualboot with two harddrives.  For example, have windows 7 professional on one and ubuntu 10.10 on the other and use the grub boot menu and also encrypt the harddrives?  Can anyone point me to a good tutorial?

---

### Post by wolfen69 on 2011-04-18
To keep things simple, you could just unplug your windows drive temporarily, install ubuntu choosing **use whole drive** during setup. Grub is automatically installed. After install, plug the windows drive back in and when in ubuntu, run

```
sudo update-grub
```
Windows will then show up in grub at bootup.
Here is a link about encryption in ubuntu. [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

---

### Post by cmb991 on 2011-04-18
That link is just referring to ubuntu.  Is there any encryption software to encrypt both the linux and windows partitions all in one shot?

---

