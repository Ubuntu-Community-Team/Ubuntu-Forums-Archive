---
title: "Dual booting and non-existent BIOS"
date: 2012-10-12
forum: General Help
---

### Post by GRX13 on 2012-10-12
I have Ubuntu and Win7 installed on a laptop and recently tried to clone a hard drive image using Clonezilla. I get a boot error and then I notice that after the Asus splash screen after pressing the laptop's power button i'm immediately taken to GRUB boot loader. 

I never have a chance to enter BIOS using F2 or F12 to select what boots first. I figure GRUB has replaced my MBR entirely. What can I do to select what boots first: from CD drive, USB or the HDD?

---

### Post by AndyOpie150 on 2012-10-12
Have you tried using the Boot Repair .iso installed onto a CD (I had to use my neighbors computer to download and burn the .iso unto a CD).

It can be found here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
:KS

---

### Post by shreepads on 2012-10-12
> **Groxxxy said:**
> I have Ubuntu and Win7 installed on a laptop and recently tried to clone a hard drive image using Clonezilla. I get a boot error and then I notice that after the Asus splash screen after pressing the laptop's power button i'm immediately taken to GRUB boot loader. 

I never have a chance to enter BIOS using F2 or F12 to select what boots first. I figure GRUB has replaced my MBR entirely. What can I do to select what boots first: from CD drive, USB or the HDD?

What does the boot error say? Mostly likely cause is that the Clonezilla boot media (CD/ USB?) is corrupt in some way so the BIOS proceeds to boot the next disk in the list, which would be your hard disk with Grub, which then presents the Grub menu.

AFAIK the MBR on a given disk is accessed AFTER the BIOS has determined the boot order. Grub overwriting the MBR should not affect your ability to enter the BIOS menu and choose boot priority...

Pls consult your laptop manual for how to trigger the BIOS menu...

---

### Post by GRX13 on 2012-10-12
The error is literally "Boot error" left justified on a black screen when I insert the Clonezilla bootable USB. The USB works on another laptop which just has Lubuntu installed. There are no indicators saying to press F2/12 after the Asus logo.

Power button > Asus logo on black screen > GRUB > Pick Ubuntu/Win7.

I'll try mashing F2/10/12 after Asus logo and if no BIOS configuration comes up i'll install Boot-repair on the Ubuntu partition and run it to reinstall a Windows compatible MBR.

Thank you for the boot-repair suggestion.

---

### Post by Mark Phelps on 2012-10-12
You have your BIOS defaults set to show the ASUS splash screen instead of the POST messages. If you can get into the BIOS setup, you should be able to change that. Either way, you should start pressing the key you want right after you press the power button -- to interrupt the POST sequence.

---

### Post by Old_Grey_Wolf on 2012-10-12
To get to the BIOS on the ASUS, press Del(ete) right after starting the computer. If that doesn't work press Ins(ert) instead.

---

### Post by GRX13 on 2012-10-16
Oh pressing Delete after powering on did bring up BIOS. So I do still have it. Was about to use boot-repair. Thank you Wolf.

---

