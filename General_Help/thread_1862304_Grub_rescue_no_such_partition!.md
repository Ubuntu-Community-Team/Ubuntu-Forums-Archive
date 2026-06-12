---
title: "Grub rescue: no such partition!"
date: 2011-10-16
forum: General Help
---

### Post by romuloarpini on 2011-10-16
Guys,

I had a partition with ubuntu and I wiped it to reinstall an older version of ubuntu. 

But, when it is booting, it gives me a "grub rescue no such partition." : (

I managed to enter on windows xp (which was in another partition) through a bootable pendrive with windows xp. I managed to enter through the recovery and tried the fixboot, fixmbr and bootcfg /rebuild, but none of them worked. 

On Windows, I saw an Ubuntu folder on C:/, dont know what should I do. Everywhere I looked it says the fixmbr command should solve, but it didnt. =/

I also saw something "wubi" in the boot.ini. Deleted this line, but still nothing. 

Is there any other way to solve this?

Best regards,

---

### Post by romuloarpini on 2011-10-16
Anyone? : (

---

### Post by bcbc on 2011-10-16
Running "fixmbr" should get windows booting.

Can you boot an Ubuntu CD in live mode (select Try It) and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") please?

---

### Post by romuloarpini on 2011-10-16
> **bcbc said:**
> Running "fixmbr" should get windows booting.

Can you boot an Ubuntu CD in live mode (select Try It) and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") please?

Thanks for your reply!

I tried fixmbr, but it didnt solve. Still this error when booting. 

I dont have a cd-rom drive : (

Any way to do that through windows or any other way to get it working?

Thanks.

---

### Post by Quackers on 2011-10-16
If you deleted a partition that had Ubuntu in it but left its grub in the mbr of the drive then grub will always try to find that deleted partition.
You need to either fix the Windows bootloader to get Windows booting again or install Ubuntu (and grub) again.
Unless as bcbc suggests, you have a wubi installation (in which case you would not actually have deleted an Ubuntu partition).

---

### Post by romuloarpini on 2011-10-16
> **Quackers said:**
> If you deleted a partition that had Ubuntu in it but left its grub in the mbr of the drive then grub will always try to find that deleted partition.
You need to either fix the Windows bootloader to get Windows booting again or install Ubuntu (and grub) again.
Unless as bcbc suggests, you have a wubi installation (in which case you would not actually have deleted an Ubuntu partition).

Yes, I used wubi to install ubuntu! Although it was a full install.

---

### Post by Quackers on 2011-10-16
As bcbc suggests, please include the output of the boot script that he links to in post #3

---

