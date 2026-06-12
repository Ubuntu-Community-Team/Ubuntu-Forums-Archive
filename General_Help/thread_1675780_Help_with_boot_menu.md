---
title: "Help with boot menu"
date: 2011-01-26
forum: General Help
---

### Post by Jamezo97 on 2011-01-26
I have recently put two hard drives into my computer, one for Ubuntu and one for Windows XP.
Anyway, I now have got everything setup on the 2 hard drives, but I have a slight problem. Whenever I want to boot into Windows or Ubuntu, i have to go into my BIOS and tell it which hard drive to boot from. Which can be a real pain in the neck.
So what i want to happen, is I want to turn on my computer, and then i want it to come up with a quick "menu" sort of thing, which asks me which  hard drive i want to boot into. Does anyone know how to do that. I know that when you have one hard drive, and you install two operating systems on it, it asks you which one you want to boot into, but how do I set it up for 2 hard drives?
Any help will be appreciated.
Thanks

---

### Post by Verbeck on 2011-01-26
boot into ubuntu and run *sudo update-grub* from a terminal (applications>accessories)
hopefully, it'll detect the windows on the other harddrive and add it to the grub menu so that you'll get a choice when you boot up the ubuntu hard-disk the next time

---

### Post by Jamezo97 on 2011-01-26
Hi, i just figured out another way to do it, which is to install "GRUB Customizer" and to go to preferences and then under visibilty to check "show menu".
That enabled the menu, but now I have another problem...
When i try to boot into windows XP, it freezes for a good 10-20 seconds, then comes up with an error message saying:

> error: no such device 36441e29441debfd.
error: invalid signature.
Press any key to continue.Any help with this one?

---

### Post by Jamezo97 on 2011-01-26
Please? I have tried many things, and all come up with the same error, or a worse one...

---

### Post by idoitprone on 2011-01-27
I only know a little about grub2, so this will might help a little bit.

find partition of windows install

```
sudo fdisk -l
```

find uuid of windows install

```
sudo blkid
```

```
sudo gedit /etc/grub.d/40_custom
```

sda1 = (hd0,1)
sda2 = (hd0,2)
sdb1 = (hd1,1) // I am not that confident of the numbering scheme for different hard drive, but I know first corresponds to harddrive # then partition number

```
menuentry "whatever name" {
        insmod ntfs
        set root=(hdwhich harddrive,parition # of window installation )
        search --no-floppy --fs-uuid --set uuid
        chainloader +1
}
```

sample

```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 8e0446680446537f
        chainloader +1
}
```

```
sudo update-grub
```

note: if you have an errors during generating grub.cfg the rest of the set of codes in grub.d folder will not execute, which means grub-mkconfig will not add 30_prober if it find an error at 10_linux

---

