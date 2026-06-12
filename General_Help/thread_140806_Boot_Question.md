---
title: "Boot Question"
date: 2006-03-07
forum: General Help
---

### Post by phargarten on 2006-03-07
2 questions:

1. When Ubuntu Loads, it doesnt load in the GUI with he progress bar, it says loading Modules and then goes into a command line type load screen. Any ideaS?

2. When booting with my bluetooth USB adapter I get the following error:

  Device Descriptor read/all error -110

Thanks for any help

---

### Post by aysiu on 2006-03-07
When it gets to the command-line, try typing ```
sudo /etc/init.d/gdm restart
```

---

### Post by phargarten on 2006-03-07
I should have reworded it. Instead of loading Linux under the orange Ubuntu logo, it goes into the primative black background; white text loading screen. So I dont get to watch the progress bar, I watch the list in huge text.

---

### Post by mr.p on 2006-03-07
[QUOTE=phargarten]2 questions:

1. When Ubuntu Loads, it doesnt load in the GUI with he progress bar, it says loading Modules and then goes into a command line type load screen. Any ideaS?

2. When booting with my bluetooth USB adapter I get the following error:

  Device Descriptor read/all error -110

Thanks for any help[/QUOTE]

In regards to 1, I have this same problem, it loads the boot splash and then crashes when it says "Loading modules" and just dumps the boot process via plain black and white terminal.

---

### Post by aysiu on 2006-03-07
[QUOTE=phargarten]I should have reworded it. Instead of loading Linux under the orange Ubuntu logo, it goes into the primative black background; white text loading screen. So I dont get to watch the progress bar, I watch the list in huge text.[/QUOTE] Oh, that!

Go to Applications > Accessories > Terminal and then ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` Add the word *splash* to the appropriate kernel line. For example, if your entry looked like this ```
title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda7 ro quiet
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot
``` you'd change it to look like this ```
title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda7 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot
```

---

