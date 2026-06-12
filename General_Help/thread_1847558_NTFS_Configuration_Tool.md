---
title: "NTFS Configuration Tool"
date: 2011-09-21
forum: General Help
---

### Post by trackmagic on 2011-09-21
Hi, I am trying to use the NTFS configuration Tool to mount my other partition at startup, but when I click on it nothing happens. I enter my password, but no application seems to open. Not sure what is going on.

---

### Post by garvinrick4 on 2011-09-21
You have to mount in fstab
```
gksudo gedit /etc/fstab
```[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
I will post my fstab in a few minutes I have a NTFS
You will need UUID 
```
sudo blkid
```(lower case L)
Use your UUID from what partition you want to mount.
My path is /media/data use your path of mounting.
Put in fstab save and reboot and will mount at boot.

# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0

## I hope this is what you are trying to accomplish.

---

