---
title: "Ubuntu 12.04 Kernel Panic with DZ77BH-55K Motherboard"
date: 2012-10-05
forum: General Help
---

### Post by cor2y on 2012-10-05
Hi all i am trying to install ubuntu 12.04 64bit edition on a system using the Intel DZ77BH-55K motherboard but regardless of what settings i disable in the BIOS or what i add to the boot menu of grub , i keep getting a kernel panic. A search of the web via google shows this board is linux compatible and in use by people using ubuntu 12.04 so for the people who have this board, what did you do to avoid/overcome the kernel panic error.

Note i have updated the motherboard BIOS to the latest one (August 2012) this didnt help, tried disabling intel virtualization, power settings etc in the BIOS as i have seen recommended for other Z77 boards (but not this one) and tried to boot with noapic etc via the grub commandline, even tried beta 2 of 12.10 to see if that would work, no go at all.

The system gets to the ubuntu live usb screen but selecting try ubuntu before installing, check disc for defects, memory test or install ubuntu results in a kernel panic and a system lock up. The live usb thumb drive is good as i tested it on another PC (this one an AMD system) it has no defects and runs fine on there.

So any help on how you overcame this problem would be appreciated.

---

### Post by speed488 on 2012-10-11
Do you get to the install menu (booted from USB/Disk)?

---

### Post by 89c51 on 2012-10-18
> **cor2y said:**
> Hi all i am trying to install ubuntu 12.04 64bit edition on a system using the Intel DZ77BH-55K motherboard but regardless of what settings i disable in the BIOS or what i add to the boot menu of grub , i keep getting a kernel panic. A search of the web via google shows this board is linux compatible and in use by people using ubuntu 12.04 so for the people who have this board, what did you do to avoid/overcome the kernel panic error.

Note i have updated the motherboard BIOS to the latest one (August 2012) this didnt help, tried disabling intel virtualization, power settings etc in the BIOS as i have seen recommended for other Z77 boards (but not this one) and tried to boot with noapic etc via the grub commandline, even tried beta 2 of 12.10 to see if that would work, no go at all.

The system gets to the ubuntu live usb screen but selecting try ubuntu before installing, check disc for defects, memory test or install ubuntu results in a kernel panic and a system lock up. The live usb thumb drive is good as i tested it on another PC (this one an AMD system) it has no defects and runs fine on there.

So any help on how you overcame this problem would be appreciated.

While i don't use ubuntu i can only assure you that this motherboard is a pain. It is NOT supported under linux from Intel which means that you are on your own. In my case it missroutes irqs and booting UEFI with any bios ohter than 057 is a no go. (havent tried the 091 though) Both these problems are firmware related and intel is not going to do anything about them. 

I was able to boot ubuntu from a CD (UEFI) only with firmware 057. On legacy mode it boots fine with other bioses but has the irq problem.

---

