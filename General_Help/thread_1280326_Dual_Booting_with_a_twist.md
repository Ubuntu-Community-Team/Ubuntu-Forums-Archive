---
title: "Dual Booting with a twist"
date: 2009-10-01
forum: General Help
---

### Post by Pyrophorus on 2009-10-01
I got a new desktop, and its running XP, I want it to dual boot with Ubuntu.

This is the twist. I want them completely independent. XP is on a
HD and Ubuntu has its own HD as well. I like to keep it that way.
Maybe a bit of merging has to be done, but I'd like to keep that
to a minimum.

---

### Post by Chronon on 2009-10-01
Is there a question?

---

### Post by dhughes on 2009-10-01
> **Pyrophorus said:**
> I got a new desktop, and its running XP, I want it to dual boot with Ubuntu.

This is the twist. I want them completely independent. XP is on a
HD and Ubuntu has its own HD as well. I like to keep it that way.
Maybe a bit of merging has to be done, but I'd like to keep that
to a minimum.

 First, put XP on the primary and then install Ubuntu on the secondary/other hard drive (choose it during install), two partitions or two drives either way works the same.

---

### Post by mechro on 2009-10-01
Your computer's BIOS may allow a choice of drive to boot from. Initial access to the BIOS depends on the manufacturer...

[http://michaelstevenstech.com/bios_manufacturer.htm](http://michaelstevenstech.com/bios_manufacturer.htm)

---

### Post by Pyrophorus on 2009-10-07
No matter which IDE cable I use, Ubuntu always boots up, I have to unplug it to use Windows. Is there a better way, to switch between
the 2 OS'?

I'm also not very familiar with GRUB, so anything detailed would be greatly appreciated.

---

### Post by oldfred on 2009-10-07
I have had a system with Sata drives now for 3 years so I may have forgotten some of the pata drive info.

I would have set the windows drive to master with either jumpers on older versions or with cable select on the end of the cable. As I remember the newer cable select cable had two colors for the connectors.
Then I would switch drives and make the ubuntu drive master and install ubuntu. It should find the windows install and only install grub to its MBR, your windows MBR will still have windows boot in it but will not be used unless your ubuntu drive fails and you switch windows back to master.

Grub allows you to select which operating system to boot without choosing in bios or switching cables, but must be installed in the MBR of the first drive that the computer will boot from.

If your already have installed both windows and ubuntu, supergrub is the best way to fix the grub boot into the MBR.  It can also repair older windows boot. You can also use the Ubuntu liveCD and instructions are just about everywhere on how to reinstall grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Pyrophorus on 2009-11-26
I have a GRUB coming up, when the computer boots up, and shows Windows
on dev/sdb

I get a signature error, whenever I try to select this. Is there anyway
to correct this?

---

### Post by Pyrophorus on 2009-11-26
I found the solution as seems to be working fine.

Thank you for all your help.

---

