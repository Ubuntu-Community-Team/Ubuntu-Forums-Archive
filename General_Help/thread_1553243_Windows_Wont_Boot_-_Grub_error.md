---
title: "Windows Wont Boot - Grub error"
date: 2010-08-14
forum: General Help
---

### Post by TrieBr on 2010-08-14
After installing linux, Windows 7 wont boot. I could do what I've done in the past which is boot the Windows recovery disk and fix the Windows boot which would essentially remove grub so I could only boot into Windows.

I forgot to take a picture of the error, but it said something along the lines of:
no such uuid <uuid>
no such parition

I'm going to edit this post with the exact error in a minute, but in the meantime, does anyone have any information on fixing the windows boot in grub?

Edit:
The error is:

error: no such device: 8a20cc1c20cc115d
error: no such partition
Press any key to continue...

---

### Post by NCLI on 2010-08-14
Try installing Ubuntu again. If Windows 7 still won't boot, start Ubuntu, open a terminal, and enter:
```
sudo update-grub
```
It will ask for your password. Enter it(It will look like nothing is being entered, that is normal), then hit enter and wait for it to finish, then restart your computer and try booting Windows 7 again.

---

### Post by TrieBr on 2010-08-14
I just tried the sudo update-grub method (I was reading around other topics and saw that), and nothing changed.

Thanks for the suggestion though ;)

I'm going to try fixing the Windows MBR using the Windows recovery disk, then I'll try booting Ubuntu liveCD and installing grub. :)

---

### Post by TrieBr on 2010-08-14
Didn't seem to work. I still get the same error that's in the original Post. I think the problem is that my Linux Partition and my Windows are on different disks with different modes (Drive with Windows is MBR, Drive with linux is GPT)

---

