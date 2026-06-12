---
title: "Grub and wundows xp"
date: 2010-02-27
forum: General Help
---

### Post by hempa on 2010-02-27
Hello i have windows xp on one of my twoo harddrives.If i choose to install ubuntu 8.04 on the other one will it detect the windows OS then and include it in the grub list? I know that it detects another ubuntu OS. Or do i have to do something after installing ubuntu so that i can choose to boot windows from the grub meny.

---

### Post by oldfred on 2010-02-27
Make the Ubuntu drive first to boot in BIOS and install. Grub should find windows and map it to make windows think it is still first and work just fine. Occasionally old grub was not as good as grub2 at finding other windows and would require some editing. If it does not work and menu.lst needs some editing but we can help if that happens. You want to keep the windows boot loader in the windows drive so that drive could still boot if necessary. If the boot drive is the windows drive grub will over write the window MBR. That can be reinstalled but is not necessary if you choose drives correctly.

There also is an advanced button on the final partition screen that lets you choose which drive to install grub to. It will default to the BIOS boot drive but I always check to make sure it installs to the drive I want.

---

