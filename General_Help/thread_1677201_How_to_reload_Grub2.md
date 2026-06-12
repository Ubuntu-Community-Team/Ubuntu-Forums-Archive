---
title: "How to reload Grub2?"
date: 2011-01-28
forum: General Help
---

### Post by gilloz on 2011-01-28
I have Vista installed on my 1st Drive.  I have Ubuntu 10.04 LTS on my second drive.(dual boot)  I am ready to replace Vista with Windows 7.  I will no longer have access to Ubuntu after I install Windows 7.  How can I get Grub2 re-install to give me the dual boot I had before?  Thanks

---

### Post by tredegar on 2011-01-28
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2011-01-28
If you have two drives you should leave the windows boot loader in the windows drive and install grub to the Ubuntu drive and set BIOS to boot the Ubuntu drive. After sudo update-grub, you should be able to boot either. With each drive independent, failure of one drive would still let you boot the other via BIOS.

---

