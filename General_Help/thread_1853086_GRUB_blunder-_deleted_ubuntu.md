---
title: "GRUB blunder- deleted ubuntu"
date: 2011-10-01
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-10-01
i am triple booting ubuntu 11.10beta2, windows 7, and backtrack 5.. all 64bit. i try to keep my GRUB menu tidy by using grub customizer to hide menu entries for previous kernels and etc so it only says: ubuntu, windows 7, backtrack 5. i must have accidentally unticked the menu entry for the newest one too, because my grub menu only says: windows 7, backtrack 5.

i have tried a couple of steps from live cd by various grub guides ive seen to restore grub and such, but they do not fix my issue and my menu stays the same. i have also booted into backtrack and ran update-grub.. it said it worked, and listed my ubuntu as oneiric ocelet beta, but it just isnt overwriting my 11.10 grub menu. upon reboot, i am greeted by my custom grub menu from 11.10 instead of a plain backtrack 5 default grub i was hoping to get.

i have also tried messing around with the etc/grub files and changed the - to a + in front of my ubuntu custom entry, but being unable to boot into that os to run update-grub, i dont know how to make the changes take effect.

any advice is welcome, even if it is to just reinstall 11.10, as i will be doing that anyways when final is released, i am just cautious to make sure it doesnt affect my other partitions. thanks in advance.

---

### Post by dcstar on 2011-10-02
> **SE7EN-LOCSTA said:**
> i am triple booting ubuntu 11.10beta2, windows 7, and backtrack 5.. all 64bit. i try to keep my GRUB menu tidy by using grub customizer to hide menu entries for previous kernels and etc so it only says: ubuntu, windows 7, backtrack 5. i must have accidentally unticked the menu entry for the newest one too, because my grub menu only says: windows 7, backtrack 5.

i have tried a couple of steps from live cd by various grub guides ive seen to restore grub and such, but they do not fix my issue and my menu stays the same. i have also booted into backtrack and ran update-grub.. it said it worked, and listed my ubuntu as oneiric ocelet beta, but it just isnt overwriting my 11.10 grub menu. upon reboot, i am greeted by my custom grub menu from 11.10 instead of a plain backtrack 5 default grub i was hoping to get.

i have also tried messing around with the etc/grub files and changed the - to a + in front of my ubuntu custom entry, but being unable to boot into that os to run update-grub, i dont know how to make the changes take effect.

any advice is welcome, even if it is to just reinstall 11.10, as i will be doing that anyways when final is released, i am just cautious to make sure it doesnt affect my other partitions. thanks in advance.

Boot the Linux OS that you want to control the machine and run this to reinstall the bootloader:

```
sudo dkpg-configure grub-pc
```

---

### Post by SE7EN-LOCSTA on 2011-10-02
thx a bunch!! i am going to post fixed.

---

