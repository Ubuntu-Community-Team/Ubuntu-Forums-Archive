---
title: "Changing GRUB from one partition to another"
date: 2009-10-31
forum: General Help
---

### Post by Cactusm123 on 2009-10-31
I've currently got a system set to dual boot Linux Mint 7 and Ubuntu Karmic. Mint was installed first, to the first partition on the drive, then Ubuntu to the second. However, I'd like to use the GRUB installed by Mint, and boot into Mint by default.

My question is thus: How can I change the MBR so that the GRUB install on SDA1 is used?

I tried going into grub in the terminal in Mint, with sudo grub, followed by:
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)

I was not sure if this would find the Mint install of Grub or the Ubuntu one, and even then if it would write to the MBR. It did not work.

---

