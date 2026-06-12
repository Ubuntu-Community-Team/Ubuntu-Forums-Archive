---
title: "Installing Nvidia hardware drivers"
date: 2009-10-29
forum: General Help
---

### Post by dyltman on 2009-10-29
Hello, I'm trying to install my nvidia hardware driver with the graphical tool however when I click on the button activate nothing happens. This has worked before and I dunno what to do. Oh and btw I'm using the new 9.10

edit: and also x64 bits.

---

### Post by celtic426 on 2009-10-29
> **dyltman said:**
> Hello, I'm trying to install my nvidia hardware driver with the graphical tool however when I click on the button activate nothing happens. This has worked before and I dunno what to do. Oh and btw I'm using the new 9.10

edit: and also x64 bits.

Check this page: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

Its a little outdated, but it has some alternative methods of installing.

---

### Post by DMK62 on 2009-10-29
Hi

From [http://www.kubuntu.org/news/9.10-release](http://www.kubuntu.org/news/9.10-release)

The "Hardware Drivers" package in Kubuntu (jockey-kde) requires a local package cache to function properly. Immediately after a new installation, this might not exist. If running jockey-kde after installing Kubuntu, first ensure there is a local package cache by running KPackageKit (K-Menu -> System Settings -> Add and Remove Software) and clicking on software updates or in a Konsole shell doing "sudo apt-get update" before running jockey-kde.

---

