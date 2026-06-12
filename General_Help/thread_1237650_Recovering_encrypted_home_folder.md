---
title: "Recovering encrypted home folder"
date: 2009-08-11
forum: General Help
---

### Post by danking12 on 2009-08-11
I have a huge issue. I recently installed Ubuntu. I had a fair bit of space left on my hard drive so I decided to dual boot and install Windows. When I installed windows I accidentally killed my MBR.

Now I can't recover my users home folder because I had encrypted it. I have the passphrase but the tutorials I found online don't seem to be working for me. Does anyone have any guide lines or steps I can follow to either recover my home folder or unencrpty it?

Thanks

---

### Post by michy99 on 2009-08-11
The first thing you should try is restoring Grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by hetx on 2009-08-11
Pop in a Live CD and follow one of the hundreds of GRUB restoring guides out there. Basically something like:

```
grub
root (hdx,x)
setup (hdy)
```

x being the partition you have Ubuntu on and y being the drive you boot from. You can find that out using:

```
sudo fdisk -l
```

Note that hd0,0 = the first hard drive, the first partition. So often sda1. GRUB counts from 0, fdisk will count from 1.

---

### Post by danking12 on 2009-08-11
Ya I should have done something like that first but instead I just wipped the partitions and reinstalled Ubuntu, with the exception of my /home partition...

---

