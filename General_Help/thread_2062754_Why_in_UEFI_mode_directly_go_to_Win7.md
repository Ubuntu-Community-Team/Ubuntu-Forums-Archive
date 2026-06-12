---
title: "Why in UEFI mode directly go to Win7?"
date: 2012-09-25
forum: General Help
---

### Post by PineWu on 2012-09-25
Hello everyone, I'm new here. I just installed Ubuntu 12.04.
I have a problem running my Ubuntu. If I set the booting mode to Legacy, it directly goes to GNU GRUB. If I set it to UEFI, it goes directly to Windows7.
I want to use these two OS interchangably. So I'd like to have a selection window before my computer runs either of these two OSs.
How should I set up Ubuntu to do that? Thanks!

---

### Post by JKyleOKC on 2012-09-25
Read this before going any farther: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

**It's essential that you know which of the two types of bootloaders your Win 7 installation is using, since the Ubuntu installation must use the same type and at the moment, the installer doesn't always make the right decision.** The link above tells you how to tell which is in use, and how to force the proper setup.

---

### Post by oldfred on 2012-09-25
If you installed the 64 bit version Boot-Repair can convert the install from grub-pc (BIOS) to grub-efi (UEFI) booting.

The 32 bit version is BIOS only and recommended by Ubuntu as many users still have old systems that will only run 32 bit systems. It is somewhat assumed that users with new system would know to install the 64 bit version as they will have a 64 bit system.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by PineWu on 2012-09-25
Sorry I'm completely new to that, although I tried to understand it seems very hard to me.

---

### Post by PineWu on 2012-09-25
> **oldfred said:**
> If you installed the 64 bit version Boot-Repair can convert the install from grub-pc (BIOS) to grub-efi (UEFI) booting.

The 32 bit version is BIOS only and recommended by Ubuntu as many users still have old systems that will only run 32 bit systems. It is somewhat assumed that users with new system would know to install the 64 bit version as they will have a 64 bit system.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Yes this works! Thanks!
I will change that to solved.

---

### Post by YannBuntu on 2012-09-27
Good job :)
For our information, please could you indicate the URL returned by Boot-Repair? (if you don't remember please follow [this tutorial]("https://help.ubuntu.com/community/Boot-Info"))

---

