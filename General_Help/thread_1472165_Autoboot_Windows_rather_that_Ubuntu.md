---
title: "Autoboot Windows rather that Ubuntu"
date: 2010-05-04
forum: General Help
---

### Post by arjunbajaj on 2010-05-04
I have installed Windows 7 on one partition (NTFS) and installed Ubuntu 10.04 on one partition (EXT4). I have one swapspace and one other FAT Partition for my data.

When i boot i get the grub screen telling me to select windows or ubuntu and some other options. Or it boots up Ubuntu after 10 seconds.......if i dont select windows......

[SIZE=3]I want that windows should boot automatically after 10 seconds rather that ubuntu[/SIZE].....How should i do that......windows is last in the list and ubuntu the first.......so i want to windows to be first and the ubuntu......so widows boots up automatically if i dont touch the keyboard.

Thnx.......

---

### Post by dcstar on 2010-05-04
> **arjunbajaj said:**
> I have installed Windows 7 on one partition (NTFS) and installed Ubuntu 10.04 on one partition (EXT4). I have one swapspace and one other FAT Partition for my data.

When i boot i get the grub screen telling me to select windows or ubuntu and some other options. Or it boots up Ubuntu after 10 seconds.......if i dont select windows......

[SIZE=3]I want that windows should boot automatically after 10 seconds rather that ubuntu[/SIZE].....How should i do that......windows is last in the list and ubuntu the first.......so i want to windows to be first and the ubuntu......so widows boots up automatically if i dont touch the keyboard.

Thnx.......

Edit the grub configuration file to use that selection. Detailed instructions are available when you do a search for a Grub2 howto.

---

### Post by dino99 on 2010-05-04
follow grub2 guide link below

---

### Post by stinkeye on 2010-05-04
Install startupmanager (gui to select boot option)
```
sudo apt-get install startupmanager
```

---

