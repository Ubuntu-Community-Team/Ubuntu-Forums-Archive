---
title: "Grub/boot problems with Zotac Ionitx in raid mode"
date: 2009-12-12
forum: General Help
---

### Post by dphreak on 2009-12-12
Hi

I have a Zotac Ionitx with two disks in raid 0 mode (with boot option checked) which doesn't seem to like grub when installing Ubuntu Server 9.10. I installed the base system with no problems, disks detected and raid activated during install, but when I got to the bootloader installation it failed. I also tried LILO, same problem. It doesn't seem to be able to install the bootloader in the mbr.

I installed Win 2008 R2 - no problem (Except the Windows part).

I know that there used to be some restrictions on the nvidia drivers on linux, but it seems to detect and use the nvidia raid without problems, but could that still be causing problems with the mbr?

I googled and did not find anything useful, so I hope someone here has some clues that can help me find and correct the problem. I know that this could be hardware, grub or installer related so I am posting here because I hope that it is only an installer issue.

Any thoughts on this problem are appreciated. Ideas on other ubuntu versions to try are also welcome.

---

