---
title: "Installing Windows XP"
date: 2006-05-25
forum: General Help
---

### Post by sprinkles on 2006-05-25
Don't worry, I'm not leaving Ubuntu, it's just my family are more comfortable with Windows.

At the moment my drive is partitioned into 2 (well, 3 if you count the swap partition). I have Windows 2000 on one partition and Ubuntu on the other.

There's a problem with my Win2k installation, so I need to format that partition and put Windows XP on it (I hate XP, but it seems Windows 2000 is being excluded more and more, so on it goes). I know that if I just use the default install WinXP is just going to write over GRUB with it's bootloader, and I won't be able to access Ubuntu.

How can I install Windows XP, but keep GRUB?

edit: forgot to say this, but I'd also like to make my Ubuntu partition a little larger at the same time if possible?

---

### Post by bruce89 on 2006-05-25
Windows has only one option - erase the whole drive, I'm afraid (I think).  You would have to back the stuff you want to keep in your breezy and install Dapper in a few days time.

---

### Post by Slim Odds on 2006-05-25
[QUOTE=bruce89]Windows has only one option - erase the whole drive, I'm afraid (I think).  You would have to back the stuff you want to keep in your breezy and install Dapper in a few days time.[/QUOTE]

Windows does not require erasing the whole disk, but it will wipe out your MBR. You need to reinstall grub after you install Windows. I don't have a link handy, but do a search for "windows MBR grub" and you should find what you need.

---

### Post by bruce89 on 2006-05-25
Use recovery mode from the Ubuntu CD (or whatever the mode is), and issue this command ```
grub-install /dev/hda
```

---

