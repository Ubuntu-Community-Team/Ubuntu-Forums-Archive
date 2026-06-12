---
title: "Win XP Home suddenly appears in grub, but I DID NOT INSTALL THIS"
date: 2011-11-03
forum: General Help
---

### Post by abendselmex on 2011-11-03
Just updated Ubuntu 10.10 - after rebooting Windows XP Home Edition appears in grub bootloader, but I did not install Windows XP Home Edition. Anybody experiencing the same?? What is this? Am I a victim of our (the german) governmental trojan, or is this just a misinterpretation of grub?????? Seriously - hard for me to go asleep now - afraid of what will go on with/on my computer after I've closed my eyes.

---

### Post by LowSky on 2011-11-03
are you joking?

Most likely it was just a error with grub

---

### Post by techvish81 on 2011-11-03
there may be some windows xp media in one of the drives , and your BIOS settings may be set to boot from it, or u may have remnants of previous installation?  very strange ¡

---

### Post by fantab on 2011-11-03
Strange indeed.

Try
```
sudo update-grub
```

Is it a laptop/desktop which had come with pre-installed XP?

---

### Post by abendselmex on 2011-11-04
Thank you for responding. It just came to my mind, that an update for grub came along with the ubuntu update. So now grub would also be capable of booting from an external usb drive, that (I am ashamed I forgot this) once indeed had a Windows Xp Home Edition on it. Sssssssss .... sorry. 

By the way - could someone please refer me to the thread, where I can find the answer about how to get Ubuntu to load properly again. Just because after the update I did 10h ago, Ubuntu got stuck with "init not found try passing init bootarg" s.o. Thanks in advance.[SIZE=3]
[/SIZE]

---

### Post by gandaran on 2011-11-04
> **abendselmex said:**
> Thank you for responding. It just came to my mind, that an update for grub came along with the ubuntu update. So now grub would also be capable of booting from an external usb drive, that (I am ashamed I forgot this) once indeed had a Windows Xp Home Edition on it. Sssssssss .... sorry. 

By the way - could someone please refer me to the thread, where I can find the answer about how to get Ubuntu to load properly again. Just because after the update I did 10h ago, Ubuntu got stuck with "init not found try passing init bootarg" s.o. Thanks in advance.[SIZE=3]
[/SIZE]
would not the ubuntu boot problem be due to the missing usb drive?

---

### Post by abendselmex on 2011-11-04
The USB drive is still connected. But anyways that's not the problem anymore.  Ubuntu won't boot with the newest Kernel - that is what's currently frustrating me (a friend is currently experiencing the same prob)

---

