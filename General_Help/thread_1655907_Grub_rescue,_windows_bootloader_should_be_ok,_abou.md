---
title: "Grub rescue, windows bootloader should be ok, about to murder everyone in this train"
date: 2010-12-30
forum: General Help
---

### Post by kaj1n3k on 2010-12-30
Ok, heres the problem. Yesterday i deleted linux partition, with grub there. Before, when i booted up ma computer, grub came first, after choosing appropriate option, win bootloader came. So minutes ago i restarted the laptop, and grub recovery console showed with error message: error: enknown filesystem. i have no live cd around, only my phone with limited inet access. I am on train, 4h away from home. The linux install was ubuntu 10.10, via classic cd(not wubi) i guess, cant remeber very well. Is theh any way i can boot up the old windows bootloader, or is it completely messed up, and i have to go all the way back home?

---

### Post by Quackers on 2010-12-30
Welcome to UF.
Sadly when you deleted an Ubuntu partition it left grub in the mbr of the hard drive. To boot Windows you will need to repair the mbr with the Windows repair disc.

---

### Post by kaj1n3k on 2010-12-30
Thanks. All the way back it is, then.

---

### Post by Quackers on 2010-12-30
I'm afraid so :-(
You have 2 choices when you get home. Repair the mbr so that Windows boots, or re-install Ubuntu and grub will be working again.

---

