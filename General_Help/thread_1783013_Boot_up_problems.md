---
title: "Boot up problems"
date: 2011-06-15
forum: General Help
---

### Post by jimbob1533 on 2011-06-15
Hi all,
Have a bit of a problem in that after some hardware changes I cant get Ubuntu to boot up anymore, even though the HDD is recognised in Bios and I can still access all files from Live CD.

Basically I have had 11.04 running for a while (from SATA hdd) and was given two IDE HDDs, one an ex external hdd, the other a windows boot which funnily enough had also had boot up problems.
After connecting up, turned on PC and it booted straight to (well tried to) windows. Realizing I had forgot to check Boot up sequence I rebooted into bios changed settings to reboot Ubuntu on original hdd and then... nothing. Just goes straight to blank screen, not even any disk activity going on.

After some playing around, putting bios back to orig settings and disconnecting ide hdds, still nothing. Although tried booting up from live cd and this works and can access files from all 3 hdds...
I am left with moving files and reinstalling but would rather not do this yet, especially if there is a quick fix!
Any help welcome!

---

### Post by jimbob1533 on 2011-06-15
Bump?

---

### Post by Phil Stone on 2011-06-15
re-install grub?  

if not then alternatively you may find that the IDE HDD's have thier jumpers* set incorrectly or are attached into the IDE cable the wrong way round - the booting disk likes to be the master where the secondary IDE hdd should be the slave. Though most current systems can auto-detect all that nowadays.

*jumpers - little plastic connectors in the pin configurations n the back of the disk by the cable socket

---

