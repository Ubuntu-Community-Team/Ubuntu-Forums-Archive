---
title: "Slow GRUB"
date: 2009-11-22
forum: General Help
---

### Post by Gannin on 2009-11-22
I just did a clean install of 9.10 and the new version of GRUB takes about 10 times as long to load and accesses the disk a lot more than the old version.  Is there any real benefit to the new version over the old version?  Is there any way to go back to using the old version?  Thank you.

---

### Post by oldfred on 2009-11-22
Do you have grub in one drive an ubuntu in a second. It is a known bug they are working on. The workaround is to install grub to the drive with Ubuntu and in BIOS switch so that drive is first.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

---

### Post by Gannin on 2009-11-22
Okay thank you, yes that's the situation I have, GRUB is on one drive and Ubuntu is on the second.  I think maybe until the issue is resolved I'll just use the old version of GRUB instead, rather than rearrange my drives in the BIOS.

---

