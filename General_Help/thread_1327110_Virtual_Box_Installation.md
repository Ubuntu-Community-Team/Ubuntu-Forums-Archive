---
title: "Virtual Box Installation"
date: 2009-11-15
forum: General Help
---

### Post by ibates on 2009-11-15
Perhaps I am a dunderhead, but I am having difficulties interpreting some installation instructions in the VB Manual.

Section 9.10.1 relates to "Access to entire physical hard disk".

The command line below is given:

VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk -rawdisk /dev/sda -register

The Guest OS (Win XP) is on a different HDD to that of the Host (Ubuntu 9.10).   I think the Win XP HDD is actually /dev/sdc1.

What would be a typical or appropriate "filename" and what actual variables would one expect to enter for "/path/to/file.vmdk"?

I assume this command would have to be entered in a terminal.  I see no opportunity to do so in the VB setup manager.

The manual assumes the user would know what was required to be entered here, but alas; my expertise is simply not up to that at this point in time.

Anyone want to have a go at straightening me out here.

---

