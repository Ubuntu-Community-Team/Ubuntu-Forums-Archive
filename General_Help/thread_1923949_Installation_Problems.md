---
title: "Installation Problems"
date: 2012-02-11
forum: General Help
---

### Post by Surouness on 2012-02-11
So my buddy burned me a disk for Ubuntu for my new laptop. I installed it so it would dual-boot (and changed the boot-priority settings and such). When I boot my computer up, I can choose either Windows 7 or Ubuntu. When I choose Ubuntu, I usually get to a few places: 1) A purple menu where I can choose to install it or 2) A screen that tells me it will install it in 5 seconds and to press [Esc] for installation options. 

The farthest I've gotten was the purple screen where I click install. It then would bring me to a purple screen that reads "Ubuntu" and five dots beneath it. That's only happened once. Mostly, I get to a confusing screen like this:

[IMG]http://handband.net/wiki/images/b/bd/LVM_Ubuntu4.gif[/IMG]

It doesn't exactly look like that. Mine usually says something along the lines of "attached ASCI disk" or something with a whole sequence of numbers like "89 e5 41 57 41 56 41 55 41 54 53 48" and "[202] terminated by signal 9" etc. I'm getting real frustrated with this wave of inconsistency in the error messages T_T Any help?

---

### Post by clausrei on 2012-02-11
If you get the GRUB boot loader asking you to choose weather Windows or Ubuntu, that means Ubuntu might be already installed. ?! Are you sure your Boots setting in your BIOS options are still set to first from CD-ROM ? Than can you start the Ubuntu on this CD as a LiveCD ?  If not, maybe you don't have a complete copy of the Ubuntu CD.  Maybe try to install Ubuntu again on the same ext3 partition.

---

