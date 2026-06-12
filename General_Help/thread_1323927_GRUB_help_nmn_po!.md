---
title: "GRUB help nmn po!"
date: 2009-11-12
forum: General Help
---

### Post by jaceleon on 2009-11-12
Can you kindly help me with the GRUB bootloader?

I happened to install Ubuntu Jaunty (I really installed it, not, make a USB persistent copy) on my 16 GB USB with 4 partitions (Ubuntu is on the 2nd partition).
Then I have the Linux Mint Live CD Persistent USB installation the 3rd drive. And I also would put DSL on the 4th partition.

How would I edit my bootloader to load those other partitions? Thanks in advance.

---

### Post by hal10000 on 2009-11-12
I suppose you configure your BIOS to boot from your usb stick by default.

Then, from the last version you are going to install on that stick you should place grub to the mbr of the usb stick (e.g. /dev/sde if that's your usb-stick's device).
Then grub should overwrite the previous mbr's on the stick while taking over previosly installed versions

---

