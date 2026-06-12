---
title: "Change splash screen ubuntu"
date: 2010-07-15
forum: General Help
---

### Post by Vishnu V on 2010-07-15
Hi
I would like to change my startup image (usplash image). For that i change /lib/plymouth/themes/ubuntu-logo/ubuntu_logo.png and /lib/plymouth/themes/ubuntu-logo/ubuntu_logo16.png. Then the splash screen of shutdown screen changes .But booting screen doesnot change. Please help me to do this

Thanks in advance

---

### Post by irw on 2010-07-15
To choose which splash screen you want:
```
sudo update-alternatives --config default.plymouth
```

Then to make it appear on boot, you need to update the initramfs:
```
sudo update-initramfs -u
```

---

### Post by Vishnu V on 2010-07-15
Thank you very much  my friend

---

