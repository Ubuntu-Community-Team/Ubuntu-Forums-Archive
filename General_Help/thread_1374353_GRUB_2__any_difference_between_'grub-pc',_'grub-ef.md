---
title: "GRUB 2 : any difference between 'grub-pc', 'grub-efi' and 'grub-coreboot'?"
date: 2010-01-06
forum: General Help
---

### Post by AlexandreP on 2010-01-06
Hi,

I would like to know if there is any differences on how to install and to configure GRUB 2 in the different architectures (BIOS/IBM PC-Compatibles, EFI/MacIntel and Corebbot)?

[LIST]
[*]Does the Ubuntu installer automatically recognize the different architectures and install the appropriate GRUB 2 package ('grub-pc', 'grub-efi' or 'grub-coreboot' according to the arch)? Or does it just install 'grub-pc'?
[*]Is the location of GRUB 2's configuration files different depending on the arch of the computer? Or are they all located in '/boot/grub/', '/etc/grub/default' and '/etc/grub.d/', no matter the arch of the computer?
[*]Are the files' structure and options to configure GRUB 2 ('/etc/grub/default' and the scripts in '/etc/grub.d/') different depending on the arch of the computer?
[/LIST]

Thanks for you help! :)

---

### Post by krazyd on 2010-04-15
Bump... I would also like to know this. :)

---

### Post by L_V on 2011-02-06
Good question.

---

### Post by srs5694 on 2011-02-06
The usual method of installing Ubuntu (at least through 10.10) on Macs uses the Mac EFI's BIOS emulation mode, so Linux thinks it's running on a BIOS-based computer and it installs grub-pc by default. I don't know offhand if Ubuntu *can* be installed directly in EFI mode on Macs. Once the system is installed, it is possible to modify it to boot in EFI mode using grub-efi; see [this Web page I wrote](http://www.rodsbooks.com/ubuntu-efi/index.html) on the topic. (Note that I've got an old 32-bit Mac Mini; there may be differences for 64-bit systems, as well as other model-to-model differences.)

I've been investigating installing the 11.04 alpha on 64-bit EFI systems, but not Macs. This version includes the ability to boot in EFI mode, but I'm not sure if this would work with 64-bit Macs. (The 32-bit version lacks EFI boot files, so unless they get added later in the development process, 32-bit Intel-based Macs will remain out in the cold on this score.) In my tests, the EFI installation works and results in a system that boots properly in EFI mode using grub-efi.

---

