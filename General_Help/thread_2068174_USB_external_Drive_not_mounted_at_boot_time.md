---
title: "USB external Drive not mounted at boot time"
date: 2012-10-08
forum: General Help
---

### Post by windyrij on 2012-10-08
Hello:
I have seen this problem on 2 systems, a new Lenovo Core i3 laptop and an older AMD64 desktop. It does not happen with Xubuntu 10.04.2 on either system.

When the system is started, the USB external hard disk is recognised (desktop icon), but not mounted. As I use Simple Backup to run every day at a fixed time, the external drive needs to be mounted. The system is not run 24/7.

The external drive can be mounted from the desktop icon, but is not mounted at boot time.
It can be mounted by unplugging the USB connection to the drive and plugging it back in.
It can also be mounted with this command in Terminal:
```
sudo mount /dev/sdb1 /media/ext_backup
```(A new folder /ext_backup was created in /media).

Running:
sudo blkid gives:
```
/dev/sdb1: LABEL="Elements" UUID="94D0D34CD0D332EA" TYPE="ntfs"
```I have added this entry to etc/fstab, using UUID. 
```
UUID=94D0D34CD0D332EA /media/ext_backup ntfs defaults
```When re-booted, the drive was not recognised (icon missing from desktop).
Now commented out.

I have installed mountmanager, which shows sdb1 as set for mount at system start.
I have worked through the USB Wizard in mountmanager, but still no luck.

Does anyone have a solution or know this is an issue which will in fixed in 12.10 or later?

I have run out of ideas, and have Googled extensively to try and find an answer, so any help would be great.

John

---

### Post by albandy on 2012-10-08
Maybe usb brings up after fstab is read.
So a startup script could do the trick.

---

### Post by windyrij on 2012-10-08
Thank you, Albandy for 
> **Re: USB external Drive not mounted at boot time**             
                                                                Maybe usb brings up after fstab is read.
So a startup script could do the trick.
You are probably right, I posted this question a couple of days ago, and failed to find it in the forum (general stupidity, I am afraid!). A reply to that post has made the same suggestion, so I'll give that a try - thanks very much
John

---

