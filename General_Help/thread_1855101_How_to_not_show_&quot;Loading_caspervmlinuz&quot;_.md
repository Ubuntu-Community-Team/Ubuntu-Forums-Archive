---
title: "How to not show &quot;Loading /casper/vmlinuz&quot; on boot"
date: 2011-10-05
forum: General Help
---

### Post by gen_u on 2011-10-05
Hello, 
 
I'm currently running Ubuntu 9.04 from a compact flash.  Is there any way to "silence" the text before the splash screen on boot?  Syslinux was used to make a bootable CF.  Upgrading to a newer version of Ubuntu is not an option at this time.  
 
Currently shows "loading /casper/vmlinuz"
                        "loading /casper/initrd.gz"
 
I would prefer that the screen was blank/black until the splash screen comes up.  Thanks!

---

### Post by dcstar on 2011-10-06
> **gen_u said:**
> Hello, 
 
I'm currently running Ubuntu 9.04 from a compact flash.  Is there any way to "silence" the text before the splash screen on boot?  Syslinux was used to make a bootable CF.  Upgrading to a newer version of Ubuntu is not an option at this time.  
 
Currently shows "loading /casper/vmlinuz"
                        "loading /casper/initrd.gz"
 
I would prefer that the screen was blank/black until the splash screen comes up.  Thanks!

You are using Syslinux to boot the system and not Grub, so you should probably go to a specialist Syslinux forum for an answer as this non-standard method is unlikely to get much assistance here.

---

### Post by lcman on 2011-10-06
> **gen_u said:**
> Hello, 
 
I'm currently running Ubuntu 9.04 from a compact flash.  Is there any way to "silence" the text before the splash screen on boot?  Syslinux was used to make a bootable CF.  Upgrading to a newer version of Ubuntu is not an option at this time.  
 
Currently shows "loading /casper/vmlinuz"
                        "loading /casper/initrd.gz"
 
I would prefer that the screen was blank/black until the splash screen comes up.  Thanks!

You need to edit the syslinux bootloader config files to prevent it from displaying anything. Look into the tars for some config files.

---

### Post by gen_u on 2011-10-06
Thanks

---

