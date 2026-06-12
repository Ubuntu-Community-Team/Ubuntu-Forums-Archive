---
title: "Side by Side installation problem"
date: 2010-02-03
forum: General Help
---

### Post by ARayRay on 2010-02-03
ok so i installed ubuntu 9.10 on an external hard drive because i wanted to be able to utilize it in addition to my windows xp media center os. the installation went fine, and i can get into either os from the grub menu, however, if the external hard drive is not plugged into my computer, it will sit at an error message, without even booting windows. i installed ubuntu on the external purely to avoid this problem. i would like to be able to travel without the external hd and still be able to boot windows. any help?

---

### Post by Ordes on 2010-02-03
your bootloader and /boot is probably on the external harddrive. so when it is not plugged in the botloader is missing its information.

>> Restore the bootloader on your hdd and you should be fine.

>> As you using an external harddrive you wouldnt need a boot menu. When USB boot is enabled in BIOS it will directly start from the external and what is on it. You only need a boot load if you have 2 OS on the HDD, or 2 OS on the external

---

