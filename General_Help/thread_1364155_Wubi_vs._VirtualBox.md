---
title: "Wubi vs. VirtualBox"
date: 2009-12-25
forum: General Help
---

### Post by Ginsu543 on 2009-12-25
This is simply for my edification. What would be the difference between installing Ubuntu using Wubi in Windows and running an Ubuntu guest in a Windows host using VirtualBox? Karmic is my main OS and I run Windows both as dual-boot (for games) and as a guest in VirtualBox, but I was curious.

---

### Post by lloyd_b on 2009-12-25
> **Ginsu543 said:**
> This is simply for my edification. What would be the difference between installing Ubuntu using Wubi in Windows and running an Ubuntu guest in a Windows host using VirtualBox? Karmic is my main OS and I run Windows both as dual-boot (for games) and as a guest in VirtualBox, but I was curious.

The main difference is performance.  Wubi does NOT run Ubuntu in a VM, but simply encapsulates the root filesystem for Ubuntu within the Windows NTFS filesystem, and then plays tricks with the startup sequence to boot Ubuntu using that encapsulated filesystem.

There's some overhead from this (having the ext3/4 filesystem encapsulated within the NTFS filesystem), but this is only on disk access, and should be substantially less than the overhead from a full host OS with a virtualization setup.

Lloyd B.

---

### Post by Ginsu543 on 2009-12-25
Thanks for the info. :)

---

### Post by abhiroopb on 2010-05-25
I currently write for a "how to" tech blog at [Make Tech Easier]("www.maketecheasier.com") (apologies for the blog spam!) and I frequently test a LOT of software for Windows 7. So, to ensure that my actual installation isn't screwed up by malware and viruses and bogged down by defunct reg keys I installed a separate Windows 7 installation in virtualbox. So, I can do anything I want inside this "sandboxed" installation without worrying about the consequences.

I was thinking about doing something similar, and I was unsure whether to go the Wubi route or the virtualbox route.

I have a fairly powerful computer so I'd rather have a "clean" way of deleting an installation that is filled with applications I have had to install over time.

Essentially, I'm not completely clear on how Wubi works and I don't want anything I do inside of Wubi (or virtualbox) to be written to my core system.

---

