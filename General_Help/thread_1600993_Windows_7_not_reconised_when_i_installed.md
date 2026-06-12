---
title: "Windows 7 not reconised when i installed"
date: 2010-10-19
forum: General Help
---

### Post by Soharuda on 2010-10-19
I figured the GRUB bootloader would know of it anyways, so i thought nothing of it when i installed Ubuntu on a seperate partition than Windows7. Now, (I dont have discs, and a my cuz let me use his, and he lost the disc), so i cant exactly just repair the MBR. Is there a way i can add it to the bootloader?

---

### Post by sikander3786 on 2010-10-19
You can boot into Ubuntu. Right?

Try these commands and post the output.

```
sudo update-grub
```

If the output lists Windows, you are good to dual boot, if it doesn't list Windows, post the output of

```
sudo fdisk -l
```

---

