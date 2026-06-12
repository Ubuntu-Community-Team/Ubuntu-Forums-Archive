---
title: "Require password when inserting my usb drive"
date: 2010-09-21
forum: General Help
---

### Post by Robert R on 2010-09-21
Hi does anyone know how to make ubuntu 10.04 ask for a password when inserting a thumb drive / flash drive .. ???

Thanks. :confused:

---

### Post by robsoles on 2010-09-22
You could encrypt the underlying file-system (look in 'System'->'Administration'->'Disk Utility' - offers to encrypt underlying file-system when you scrub a drive and re-partition it) or you could re-format the drive in ext4 and set it as 'owned' by you.

It is weaker to use the second method I suggest because pretty sure 'root' on any system can override your permissions if the USB stick is inserted to that system whereas with the encrypted file-system it takes a good deal more work on anybody's behalf to gain access to it without your passphrase.

---

### Post by Robert R on 2010-09-22
I understand but its really the information on the laptop im trying to protect from being copied as it is very sensitive so my goal is to password protect the usb Bus so that if a thumb drive / external HD or media  is inserted  then you need the password to gain access to the media. Do you think you can help with that.??

---

### Post by BobVila on 2010-09-22
> **Robert R said:**
> I understand but its really the information on the laptop im trying to protect from being copied as it is very sensitive so my goal is to password protect the usb Bus so that if a thumb drive / external HD or media  is inserted  then you need the password to gain access to the media. Do you think you can help with that.??

I'd encrypt the filesystem on the laptop if that's your endgame. If someone's got local access to the system, the USB ports will be the least of your worries (network, livecd, etc.)

---

### Post by Robert R on 2010-09-22
but if i do encrypt the file system and the HD were to crash or summin would i be able to go on another computer and access the data??

---

### Post by BobVila on 2010-09-22
> **Robert R said:**
> but if i do encrypt the file system and the HD were to crash or summin would i be able to go on another computer and access the data??

It's a pain in the rear, but yes.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually")

Gotta compromise somewhere, though. Locking the USB ports down would be more an illusion of security than anything, imo.

Then again, if the HDD crashes, it crashes. Encrypted or not, you're going to be in for a headache.

---

### Post by robsoles on 2010-09-22
You could switch to keeping the sensitive data on two encrypted external HDDs that you would have to sync - this way if one bombed it you just replace it etc etc.

---

### Post by sisco311 on 2010-09-22
EDIT:

Create a new .pkla file:
```
gksu gedit /var/lib/polkit-1/localauthority/50-local.d/mount-usb.pkla
```
with the following content:
```
[Mounting, checking, etc. of external drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-mount;org.freedesktop.udisks.filesystem-check;org.freedesktop.udisks.filesystem-unmount-others;org.freedesktop.udisks.drive-eject;org.freedesktop.udisks.drive-detach;org.freedesktop.udisks.change;org.freedesktop.udisks.luks-unlock
ResultActive=auth_admin_keep
```

---

### Post by Robert R on 2010-09-23
ill try what sisco311 commands and see if that works. if not then i will try to sync my external HD. If i do however have to sync do you know of any programs that would be helpful in this. 

Thanks for all your helps again.

---

