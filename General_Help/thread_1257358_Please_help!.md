---
title: "Please help!"
date: 2009-09-03
forum: General Help
---

### Post by shannon7287 on 2009-09-03
I recently installed UBUNTU on my computer.  I didn't dual boot it with anything ...I just have ubuntu taking up the entire disk space....Now I realized I don't want it anymore and it won't allow me to boot from my xp cd because it keeps going to ubuntu.  I was reading in other forums and I know I have to delete grep in order for it too boot from my XP cd so I can install XP again... I have no idea how to remove it.  I tried using the super grub cd and nothing is working.. I really would appreciate if someone could supply me with step by step instructions on how to remove this.  PLEASE!

- THANKS

---

### Post by Iowan on 2009-09-03
Do you have the opportunity to edit the BIOS? You *might* be able to change the boot order so CD boots first.

---

### Post by Vaphell on 2009-09-03
in BIOS there is a configuration of booting sequence. If you want to boot from CD, you must set it to have CD drive before the hard drive.
If it is set properly, any bootable CD should work - i assume XP disc is bootable.
If i remember correctly there should be some 'Press any key to boot from CD' message when you start your computer, just after BIOS check. Pressing anything in that brief period of time should show the CD menu - you just delete any partitions, create one or more for windows and allow installer to do its thing. It will erase any trace of grub so you don't have to worry about that.

---

