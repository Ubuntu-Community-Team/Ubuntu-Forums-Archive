---
title: "No Disc space"
date: 2010-12-29
forum: General Help
---

### Post by woodsculpture on 2010-12-29
I just installed Ubuntu via Wubi along side Windows XP.  When I clicked on my update notice, I got the following error message:

[CENTER]Not enough free disk space
[/CENTER]

The upgrade needs a total of 62.9M free space on disk '/'. Please free at least an additional 62.9M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I just checked and discovered that only 2.3G were allocated for the installation.  Is there any way I can increase this?

---

### Post by davidmohammed on 2010-12-29
given that it is wubi - I would suggest you boot into windows - remove wubi via add/remove programs and this time, reinstall, but this time give it more disk space.

This would be - I would suggest - much faster.

There are instructions [here]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?") how to increase the virtual disk size - but that just seems a lot of work!

---

### Post by woodsculpture on 2010-12-29
Something that I neglected to mention before is that on my initial install, I accidentally deleted a file for the GRUB and had to do a reinstall.  The reinstall seemed to take very little time, could I have messed up the Wubi file?

---

