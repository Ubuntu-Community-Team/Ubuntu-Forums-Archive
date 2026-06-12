---
title: "Boot issues - NTFS error?"
date: 2010-10-24
forum: General Help
---

### Post by caladin on 2010-10-24
10.10

Was messing aroudn with ntfs permissons on a second drive I installed. For some reason when I rebooted I got this error and now it wont boot.

Ext4-FS (SDA1) Unreconized mount option "nls=utf8" or missing value

Any ideas on how to fix this with out rebuilding from scratch. Im a newbie so go easy :)

---

### Post by mcduck on 2010-10-24
I suppose you were messing with the /etc/fstab file?

Just boot the computer with a live-CD (or USB drive), and fix the fstab. Based on the error you now have "nls=utf8" as an option for one of your Ext4 filesystems. Just remove that option, it's for NFTS only.

---

### Post by argedion on 2010-10-24
You'll have to be more specific to what "Messing around with permissions" means and is it possible to go into a live environment using a program like UBCD4Win? Did you have Grub loaded on the Drive? Is the primary drive bootable? Are you using Windows XP / Vista / 7?

---

### Post by caladin on 2010-10-24
> **argedion said:**
> You'll have to be more specific to what "Messing around with permissions" means and is it possible to go into a live environment using a program like UBCD4Win? Did you have Grub loaded on the Drive? Is the primary drive bootable? Are you using Windows XP / Vista / 7?

Primary drive on ubuntu is not bootable. It was trying to mount a drive from a Windows 7 box. I was looking at "NTFS permisson" option since I thought it was the issue why I could not mount. I tried to mount it and it would not let me. Its a non bootable drive. Just a drive I had some files on I wanted to scan with clam.

What should it say in the fstab on that line?

---

### Post by argedion on 2010-10-24
> Primary drive on ubuntu is not bootable. It was trying to mount a drive from a Windows 7 box. I was looking at "NTFS permisson" option since I thought it was the issue why I could not mount. I tried to mount it and it would not let me. Its a non bootable drive. Just a drive I had some files on I wanted to scan with clam.

What should it say in the fstab on that line? 

I'm not sure what you have done but answer me this:

Was the drive you messing with NTFS or EXT 2,3,or 4? Windows itself wont show a linux drive without help from a driver or other third party program. Windows drive manager will show the drive and usually and UNKNOWN file system attribute.

> Ext4-FS (SDA1) Unreconized mount option "nls=utf8" or missing value

Boot to a Live CD / USB and navigate to the hard drive your install is on got to etc  and find the file fstab on the hard drive line and just remove the line nls=utf8 then try to boot normally.

---

### Post by caladin on 2010-10-24
> **argedion said:**
> I'm not sure what you have done but answer me this:

Was the drive you messing with NTFS or EXT 2,3,or 4? Windows itself wont show a linux drive without help from a driver or other third party program. Windows drive manager will show the drive and usually and UNKNOWN file system attribute.



Boot to a Live CD / USB and navigate to the hard drive your install is on got to etc  and find the file fstab on the hard drive line and just remove the line nls=utf8 then try to boot normally.

The drive I was trying to mount on my ubuntu box was ntfs. 

I did boot to the live CD and went to the drive, mounted it and then attempted to edit the fstsab file. It told me I dont have permisson to edit. I am using nano and Im in as root.

---

### Post by caladin on 2010-10-25
How do I resolve the permissons issue. It states that it is a read only file.

---

### Post by mcduck on 2010-10-26
it's highly unlikely that you'd be logged in as root, considering that Ubuntu doesn't even use root account by default and enabling that on a live-CD would be a bit of a trick... ;)

So, you get around the permissions exactly as you'd do the same thing on a installed Ubuntu system, by using "sudo".

```
sudo nano /etc/fstab
```

Reading this would probably make your life a bit easier: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

