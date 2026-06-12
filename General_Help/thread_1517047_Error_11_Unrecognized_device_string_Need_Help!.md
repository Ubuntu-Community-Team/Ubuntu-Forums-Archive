---
title: "Error 11: Unrecognized device string Need Help!"
date: 2010-06-24
forum: General Help
---

### Post by flare243000 on 2010-06-24
ok im new so sorry if this has been posted before or is in the wrong spot. i downloaded backtrack 4 (final) and booted the iso onto a flash drive using unetbootin. i then changed the boot order so the flash drive was first. after i did that i got into backtrack 4 did the install.sh and now i cant boot windows 7. even after changing the boot order to default, i turn my computer on and get a message that says:



Ubuntu 8.10, kernel 2.6.30.9
Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
Ubuntu 8.10, memtest86+
Other operating systems :
Memory Test (on /dev/sda1)
Ubuntu 8.10, kernel 2.6.30.9 (on dev/sda1)
Ubuntu 8.10, kernel 2.6.30.9 (recover mode) (on dev/sda1) 
Ubuntu 8.10, memtest86+ (on dev/sda1)




_________________________________________________________________________________________________
use the [up arrow symbol] and [down arrow symbol] keys to select which entry is highlighted. 
Press enter to boot the selected OS, 'e' to edit the commands before booting, or 'c' for the command-line.





And when i select: Other operating systems : i get:


Error 11: Unrecognized device string

Press any key to continue..._






i can only boot backtrack 4 OS, i really want to know what can i do to be able to boot my windows 7 home premium os.

---

### Post by VH-BIL on 2010-06-24
If you are using grub as your boot loader you can try:
```
sudo update-grub2
```
or
```
sudo update-grub
```
depending on what version you are using.

---

### Post by flare243000 on 2010-06-24
> **VH-BIL said:**
> If you are using grub as your boot loader you can try:
```
sudo update-grub2
```or
```
sudo update-grub
```depending on what version you are using.

where should i put these codes in?

---

