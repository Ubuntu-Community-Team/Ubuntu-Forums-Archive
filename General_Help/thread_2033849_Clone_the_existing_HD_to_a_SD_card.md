---
title: "Clone the existing HD to a SD card"
date: 2012-07-27
forum: General Help
---

### Post by wilsonmak on 2012-07-27
I like to clone the existing 80G HD (around 4G including system + data) to a 16G SD card.  Then I can boot from SD card instead of HD.

1) I try using Clonzilla and make an image and then restore to a SD card, but it got lots of error messages.  

2) I try dd if=/dev/sda of=/dev/sdb bs=4M (not enough space???)

3) Create partition on SD card and copy the existing stuffs from HD to SD. Of course it can't boot.  Need to edit grub2 entries?

Or any other good ways to do it?

Thanks,
Wilson

---

### Post by wilsonmak on 2012-07-27
P.S. It's installed Ubuntu 10.10 on the existing HD!

---

### Post by dcstar on 2012-07-27
Use a Live CD & **gparted** to shrink the existing partition to a size that will fit on the card.

---

### Post by oldfred on 2012-07-27
dd also copies empty space & intended for exact size to exact size image copy. So it tried copying all 80GB.

I prefer clean install and copy /home with rsync to new install. If trying to boot from an imaged drive and still have original mounted you will have issues of duplicate UUIDs. Then you have to change UUIDs,  update fstab, reinstall grub2 and some other internal settings to make UUIDs correct.

Only a few newer systems directly boot from SD cards. Have you checked that yours does boot? Most do boot from USB flash drives.

---

### Post by wilsonmak on 2012-10-16
Thank You all! It works!

---

