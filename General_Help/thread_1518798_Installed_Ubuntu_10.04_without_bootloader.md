---
title: "Installed Ubuntu 10.04 without bootloader"
date: 2010-06-27
forum: General Help
---

### Post by garfieldwasacat on 2010-06-27
Hi everyone

I've just installed Ubuntu 10.04 on a separate partition with Windows 7 also active on the drive.

I chose not to install the Ubuntu boot loader because I wanted to use Windows' own and I didn't want Ubuntus to interfere.

When I restart the system Windows loads automatically with no sign of Ubuntu.

I tried to go into the Windows settings from the GUI 2 different ways and Ubuntu was not listed.

Is there any way I can get Windows to recognize that Ubuntu is installed or do I need to install the Ubuntu bootloader?

Thanks

---

### Post by dino99 on 2010-06-27
Crozoft dont promote other OS :p

that should not be a surprise, dont you ?

---

### Post by teilnehmer on 2010-06-27
garfieldwasacat, 

let me extend on what dino99 said. It's not possible to boot Ubuntu with a Windows bootloader, because Windows won't recognize other OSs. 
When you say you wanted to use the Windows bootloader, can you explain what you mean? If only Win7 is active, why would there be a bootloader?

---

### Post by jocko on 2010-06-27
> **teilnehmer said:**
> When you say you wanted to use the Windows bootloader, can you explain what you mean? If only Win7 is active, why would there be a bootloader?
Of course windows 7 have a boot loader. It's just that the windows boot loader is not advanced enough to be able to detect a linux os. But it should be possible to edit the boot.ini file (which contains the windows boot menu, at least in XP) to get it to load grub on another partition.

---

### Post by Leppie on 2010-06-27
ubuntu requires a more sofisticated boot loader than the windows one. you should install grub (or another boot loader able to boot linux) to the boot sector of the ubuntu partition.

there are ways to add ubuntu to the boot manager with bcdedit, search this forum for it as there are several threads.
or otherwise there's sites like neosmart (excellent resource for windows utilities):[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Edit: i dual boot several machines with 7 and Ubuntu with grub2 as the boot loader, no problems at all.

---

### Post by philinux on 2010-06-27
> **garfieldwasacat said:**
> Hi everyone

I've just installed Ubuntu 10.04 on a separate partition with Windows 7 also active on the drive.

I chose not to install the Ubuntu boot loader because I wanted to use Windows' own and I didn't want Ubuntus to interfere.

When I restart the system Windows loads automatically with no sign of Ubuntu.

I tried to go into the Windows settings from the GUI 2 different ways and Ubuntu was not listed.

Is there any way I can get Windows to recognize that Ubuntu is installed or do I need to install the Ubuntu bootloader?

Thanks

Easybcd does the job on my GF's lappy. I installed grub to the ubuntu partition to achieve this though.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by prodigy_ on 2010-06-27
> **teilnehmer said:**
> It's not possible to boot Ubuntu with a Windows bootloader
Of course it's possible. Not directly but you can chainload Grub from BCD just as you chainload BCD from Grub. How about using forum search before posting?

---

### Post by philinux on 2010-06-27
> **teilnehmer said:**
> garfieldwasacat, 

let me extend on what dino99 said. It's not possible to boot Ubuntu with a Windows bootloader, because Windows won't recognize other OSs. 
When you say you wanted to use the Windows bootloader, can you explain what you mean? If only Win7 is active, why would there be a bootloader?

Thats exactly what easybcd does, please research easybcd. 

But grub has to exist on the target partition.

---

### Post by garfieldwasacat on 2010-06-27
I guess it is important to install grub with the Ubuntu installation regardless if I wanted to use it or not

from there I will then try and switch to the Windows boot loader or stay with grub

Thanks for all the help and the links

---

### Post by Leppie on 2010-06-27
> **garfieldwasacat said:**
> I guess it is important to install grub with the Ubuntu installation regardless if I wanted to use it or not
it doesn't have to be grub per se, but a boot loader capable of launching your linux which bcd obviously is not.

---

