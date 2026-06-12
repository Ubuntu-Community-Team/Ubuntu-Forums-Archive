---
title: "Grub Finds Windows, Doesn't Show It"
date: 2010-03-27
forum: General Help
---

### Post by chessnerd on 2010-03-27
So I installed and am now testing Kubuntu 10.04 on a desktop computer I recently got from my aunt. So far Lucid seems stable and everything under Linux is working fine. However, I noted this morning that my Grub menu at boot-up no longer shows the Windows XP partition.

First, I tried updating grub and it showed that it found Windows and the grub.cfg file had the Windows information in it so I thought the problem was solved. Rebooted and still nothing.

Here is the menu entry as it looks in the grub.cfg file:
```
menuentry "Microsoft Windows XP Home Edition" {
        insmod ntfs
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8eb4c3eeb4c3d73d
        drivemap -s (hd0) ${root}
        chainloader +1
}
```

This menu entry looks okay, so I'm not sure what the problem is, but I'm not an expert on Grub in any way. 

If any addition information is needed please let me know. Thanks.

---

### Post by chessnerd on 2010-03-27
Alright, I seem to have fixed the problem, but I don't know why...

I disabled the 20_Memtest86+ file by making it non-executable and then Grub worked. I'm not sure what the issue is, but I'm glad that my dual-boot is working again.

---

