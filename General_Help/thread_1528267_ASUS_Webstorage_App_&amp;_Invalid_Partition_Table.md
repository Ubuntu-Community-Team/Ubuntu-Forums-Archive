---
title: "ASUS Webstorage App &amp; Invalid Partition Table"
date: 2010-07-10
forum: General Help
---

### Post by dccrens on 2010-07-10
I have a Ubuntu 9.10 system desktop that has been rock stable. It is dual boot with Windows XP. I just signed up for the ASUS Webstorage similar to dropbox. They have an Ubuntu version (in a .deb) so I dl'ed that and installed. Installed fine. I ran the app and it seemed to bring up a file browse window in a "mounted" partition with ASUS information in it. Couple of shells to display their web site. My assumptions was this was network mounted storage area. So after that, I rebooted the machine and instead of system my grub menu, I get:

"Invalid Partition Table!"

Anyone else run into this?

---

### Post by dccrens on 2010-07-11
After messing with grub2 for a day, and having nothing work, I finally tried switch the boot drive in the computer bios. Low and behold that worked! somehow in installing the ASUS software and rebooting the boot drive in the bios was changed. No idea how.

---

