---
title: "Need help with booting windows 7 iso from Grub2"
date: 2009-10-24
forum: General Help
---

### Post by samuelhug on 2009-10-24
Hi I'm currently running Karmic and would like to dual boot with Windows 7. I have the windows 7 iso and no DVD to burn it to so I was wanting to boot directly off the iso.

I tried the following

```
loopback loop /boot/win7-pro.iso
chainloader (loop)
```

And I received the following error
```
error: invalid file name `'
```

Any help in doing this would be greatly appreciated.

---

### Post by sailthesea on 2009-10-24
You could set up a VM with Karmic and try Win 7 on that but I think its only going to work well if you install on your primary partition
 Maybe put the ISO on a USB then dual boot?

---

### Post by samuelhug on 2009-10-24
Unfortunately my usb boot broken.

I was planing on loosely following [these]("http://ubuntuforums.org/showthread.php?t=1035999") instructions.

---

### Post by sailthesea on 2009-10-24
> **samuelhug said:**
> Unfortunately my usb boot broken.

I was planing on loosely following [these]("http://ubuntuforums.org/showthread.php?t=1035999") instructions.


That would certainly worth a try:)

---

