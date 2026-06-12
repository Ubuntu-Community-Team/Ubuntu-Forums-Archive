---
title: "install grub to /boot"
date: 2012-03-15
forum: General Help
---

### Post by PhantomTurtle on 2012-03-15
I want to install grub to /boot instead of MBR (its because I want to dual boot with Windows 7). I also need to do this with the alternative installer. I found this thread ([http://ubuntuforums.org/showthread.php?t=781746]("http://ubuntuforums.org/showthread.php?t=781746")), it says there is a way to do it but I have not seen an option to do it in the ALTERNATIVE INSTALLER.

Thanks in advance for any help.

---

### Post by SystemsGO on 2012-03-15
> **PhantomTurtle said:**
> I want to install grub to /boot instead of MBR (its because I want to dual boot with Windows 7). I also need to do this with the alternative installer. I found this thread ([http://ubuntuforums.org/showthread.php?t=781746]("http://ubuntuforums.org/showthread.php?t=781746")), it says there is a way to do it but I have not seen an option to do it in the ALTERNATIVE INSTALLER.

Thanks in advance for any help.


Have you already installed your dual boot? If so, what happens when you boot up?

---

### Post by PhantomTurtle on 2012-03-15
> **SystemsGO said:**
> Have you already installed your dual boot? If so, what happens when you boot up?

I haven't installed yet. I wanted to know how to do it in the alternative installer.

---

### Post by SystemsGO on 2012-03-15
I'm unsure how to do it in the alternative install, but you should be able to run the install cd, and select "install alongside Windows 7", then make your partitions(it's easy). If any problems arise, you can always do a boot-repair.

---

### Post by PhantomTurtle on 2012-03-15
I figured it out. After the the disk partitioning is done and ubuntu is installed, the installer will ask you if you want to install to the MBR or to a different partition. After that you can just use easybcd to add Ubuntu to the boot menu.

---

