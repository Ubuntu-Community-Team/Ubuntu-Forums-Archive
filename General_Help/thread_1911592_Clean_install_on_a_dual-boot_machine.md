---
title: "Clean install on a dual-boot machine"
date: 2012-01-19
forum: General Help
---

### Post by veggen on 2012-01-19
Hi all.
I currently have a dual boot XP and Ubuntu 10.10 (on the same HD), and I want to cleanly install the latest Ubuntu over the old one. But, I'm not sure how to do that. If I just wipe clean the partition where Ubuntu resides and install the new one there, will it be enough? Will it still be able to boot XP afterwards? Do I need to do anything about swap partition or can I just leave it as-is?

Thanks.

---

### Post by nothingspecial on 2012-01-19
First make a backup of all your data.

Boot up the live cd/usb.

Start the installer and when it asks you how you want to install Ubuntu choose "something else"

The partitioner will start and you will see your windows and ubuntu partitions. Ubuntu will be an ext4 file system. Choose that one to edit.

Choose to format it.
Choose to use it as an ext4 journaling file system.
Choose a mountpoint of /

The installer should recognise your swap but you can check if you like.

**[COLOR="Red"]Do not touch your windows/ntfs partition[/COLOR]**

That's it.

---

### Post by nipunshakya on 2012-01-19
> **veggen said:**
> Hi all.
I currently have a dual boot XP and Ubuntu 10.10 (on the same HD), and I want to cleanly install the latest Ubuntu over the old one. But, I'm not sure how to do that. If I just wipe clean the partition where Ubuntu resides and install the new one there, will it be enough? Will it still be able to boot XP afterwards? Do I need to do anything about swap partition or can I just leave it as-is?

Thanks.
hi. i have the similar scenario too but only difference is **used to have** Windows 7 and Ubuntu 11.10 OSs on different partitions. I didnt like the new 11.10 so i downgraded to 11.04. For that i did the following:
1. Booted windows 7 and ran Disk Management utility from there.
2. Formatted all my linux partitions.
3. Restarted.......and then, i got the grub rescue error.......But then, i didn't panic.
4. Realizing that i **could have created a startup disk creator at the beginning, **i didn't and so i had only option to reinstall via a LiveCD...and i did so.
5. I made clean partitions again,(didn't touch even a byte of windows 7 partitions! ) and then reinstalled Ubuntu 11.04 successfully. And now, im suggesting the same for u via my fresh Ubuntu 11.04 

Goodluck.
Regards,WinuxUser

---

### Post by veggen on 2012-01-19
Ok, thank you both a lot! Sounds easy enough and pretty much what I expected. Btw, my Ubuntu is now on ReiserFS but I'll create an ext4 when reinstalling (as the reason for ReiserFS no longer applies).

---

### Post by nipunshakya on 2012-01-19
> **veggen said:**
> Btw, my Ubuntu is now on ReiserFS but I'll create an ext4 when reinstalling (as the reason for ReiserFS no longer applies).
Sounds like a better idea. Happy installation. Goodluck.

Regards,WinuxUser

---

