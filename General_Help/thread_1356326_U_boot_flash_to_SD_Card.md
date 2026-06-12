---
title: "U boot flash to SD Card"
date: 2009-12-15
forum: General Help
---

### Post by shariefbe on 2009-12-15
Hello,
    I am using ARM based board. I want to boot the kernel from SD Card. For that i have to install the u boot bootloader into SD card. how to install u boot from host computer? i have partitioned my SD card into 3. i have to install u boot in first partition. So please kindly help me.

---

### Post by chenxiaolong on 2009-12-21
Install these packages:

```
chenxiaolong@d6657k1:~/tmp$ sudo apt-cache search uboot
[sudo] password for chenxiaolong: 
uboot-mkimage - generate kernel image for U-Boot
uboot-envtools - read/modify the environment for the bootloader U-Boot
chenxiaolong@d6657k1:~/tmp$ 

```

---

### Post by shariefbe on 2009-12-22
ok how to install that uboot image to SD card. Its not working properly when i copied

---

