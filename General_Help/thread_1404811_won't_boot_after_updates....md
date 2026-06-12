---
title: "won't boot after updates..."
date: 2010-02-11
forum: General Help
---

### Post by CntdwnToExtn on 2010-02-11
hello,

i just did a fresh install of 9.10 and after running and installing the updates (222) i rebooted but ubuntu will no longer load.
2.6.31-14
2.6.31-19
as well it hangs on the recovery too. this is the last line:
```

ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-oxb0f]

```

not really sure what to do here :S

---

### Post by colobix on 2010-02-11
Have you tried the older kernel?
YOu could try to restore your grub backup file;

```

sudo mv /media/disk/boot/grub/menu.lst /media/disk/boot/grub/menu.lst.bad
sudo cp /media/disk/boot/grub/menu.lst.backup /media/disk/boot/grub/menu.lst

```

---

### Post by CntdwnToExtn on 2010-02-11
yes, i've tried both kernel's as well both for recover.
grub 1.97 beta 4 it says at the top

heh, how do i go about that? i'm quit the beginner... :)

---

### Post by colobix on 2010-02-11
You have the live cd you used to install ubuntu right?
Ok, run the live cd and go to terminal and run the two commands
```
sudo mv /media/disk/boot/grub/menu.lst /media/disk/boot/grub/menu.lst.bad
sudo cp /media/disk/boot/grub/menu.lst.backup /media/disk/boot/grub/menu.lst
```

This will give you your old grub menu back.

If that doesnt work, well then the problem is probably that your kernels hasnt been updated after the installation so if that's the case you gonna have to reinstall Grub.

But try to restore your backup and come back if that doesnt work.

---

### Post by CntdwnToExtn on 2010-02-12
I will try that colobix.
I'm at work right now will run that when I get home later today.
Thanks.

---

