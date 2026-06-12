---
title: "Grub2 NOT on boot sector"
date: 2010-02-08
forum: General Help
---

### Post by momalle1 on 2010-02-08
I have a dual boot Win7 and Ubuntu 9.10. Despite selecting GRUB to install on my EXT4 partition during setup, it installed itslef tot eh boot sector. I manually installed it where I wanted it and reinstalled the Win7 boot sector. Everything works well and I launch Ubuntu via an entry created by EasyBCD. The problem is that every time Updates has a new kernel, it runs grub setup and installs Grub2 to the boot sector. GRUB2 is not as easy to remove as GRUB was, and it's just a PITA to go through this every time an updated kernel gets installed. Is there any way I can deter this behavior?

---

### Post by meierfra. on 2010-02-08
Just run this command in  a terminal in Ubuntu:


```
echo "set grub-pc/install_devices"  | sudo debconf-communicate
```

and "grub-install" will no longer run during updates.


Or you can use 

```
echo "set grub-pc/install_devices  /dev/sdXY" | sudo debconf-communicate
```

to have Grub installed to the boot sector of "/dev/sdXY"

Before you change the setting, you might want to have a look at the current settings via:

```
echo "get grub-pc/install_devices" | sudo debconf-communicate
```

---

### Post by momalle1 on 2010-02-09
Thank you so much!

Having grub install to where I wanted it worked like a charm, thanks again!

---

