---
title: "Blinking cursor after grub - recovering a damaged VM Ubuntu server"
date: 2011-06-06
forum: General Help
---

### Post by Illuma on 2011-06-06
I have an Ubuntu server virtual machine running in vmware server on a Win2003 server host. A locked up machine forced a hard reset a couple of days ago and my VM seems to be damaged.

At first VMware wouldn't start the VM, complaining of a locked file. I deleted 3 .lck directories and was able to start up the VM. I then get a GRUB menu with 6 options - booting any of them other than memtest results in a lone underscore cursor at the upper left corner.

Could someone point me in the right direction as far as the next thing I should try at this point? Unfortunately I had not yet set up a rigorous backup scheme, other than internal daily db/web backups that are stored inside the VM. I have a snapshot from 3 weeks ago but upon loading the snapshot I get the same cursor.

---

### Post by Illuma on 2011-06-08
I was able to solve this issue, apparently VT-X had been disabled on the host machine and therefore VMWare could no longer run 64bit guests. Copied the VM to another server and it booted up just fine.

---

