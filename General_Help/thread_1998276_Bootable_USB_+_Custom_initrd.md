---
title: "Bootable USB + Custom initrd"
date: 2012-06-06
forum: General Help
---

### Post by ciclonite on 2012-06-06
Hi all, This is my first post.. 
I've a usb stick that have one partition public and one partiton  "private" with the hw capabilities to encrpyt/decrypt the private  partition with AES. For decrypt the partition i need to use the  proprietary api of the device. On the public partition i've installed  syslinux that call initrd, at this point initrd call the small program  that ask for the password and ,if the password is correct, unlock the  private partition and load root patition. Only a question: it's possible  to do this or i've missing something?

---

