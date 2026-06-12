---
title: "How to install GRUB on an already dual boot system?"
date: 2009-11-11
forum: General Help
---

### Post by Cool G5 on 2009-11-11
I'm confused as to where to put this thread so I begin it here. Mods please move it if you find this section incorrect.

My friend had Linux Mint 7 & Windows XP Pro installed on his computer. He has a 500GB SATA Hitachi HDD. My 640GB WD HDD was giving me Grub Error 22, so I took the drive & connected it to his PC as a second drive. Next I inserted Windows XP, went to Repair Mode & issued a fixmbr command to clear the boot record of my drive. After that I disconnected my HDD & booted his PC but now the PC didn't gave any option to select between Windows XP & Linux Mint 7. I booted via Sabayon Linux 5 & I saw the Linux Mint partitions on his HDD. I think my command cleared up the GRUB & the boot entry of Linux Mint 7. How can I get it back so that once again the PC becomes dual boot?

---

### Post by mehaga on 2009-11-11
Try this
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Or browse to it:
Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Tutorials & Tips > How to install Grub from a live Ubuntu cd.

---

### Post by Cool G5 on 2009-11-12
I'm getting the following,

> Invalid Device Request.

---

### Post by ZankerH on 2009-11-12
Use the [Super Grub Disk](http://www.supergrubdisk.org/)

---

### Post by MasterNetra on 2009-11-12
> **Cool G5 said:**
> I'm confused as to where to put this thread so I begin it here. Mods please move it if you find this section incorrect.

My friend had Linux Mint 7 & Windows XP Pro installed on his computer. He has a 500GB SATA Hitachi HDD. My 640GB WD HDD was giving me Grub Error 22, so I took the drive & connected it to his PC as a second drive. Next I inserted Windows XP, went to Repair Mode & issued a fixmbr command to clear the boot record of my drive. After that I disconnected my HDD & booted his PC but now the PC didn't gave any option to select between Windows XP & Linux Mint 7. I booted via Sabayon Linux 5 & I saw the Linux Mint partitions on his HDD. I think my command cleared up the GRUB & the boot entry of Linux Mint 7. How can I get it back so that once again the PC becomes dual boot?

Trying to use WinXP to fix a grub issue is a no-no. The fixmbr command clears whatever controls boot and replaces it with Window XP's booter which never checks for non-window based Operating Systems and thus would never give you boot options for Mint. This is why when setting up a dual boot you install windows first then Linux. Sense Grub will recognize windows (or should) and give you options.

---

### Post by Cool G5 on 2009-11-16
> **MasterNetra said:**
> Trying to use WinXP to fix a grub issue is a no-no. The fixmbr command clears whatever controls boot and replaces it with Window XP's booter which never checks for non-window based Operating Systems and thus would never give you boot options for Mint. This is why when setting up a dual boot you install windows first then Linux. Sense Grub will recognize windows (or should) and give you options.

Thanks for the info :) I didn't knew this.

By the way, I restored GRUB by using Fedora 11 DVD. :D

---

