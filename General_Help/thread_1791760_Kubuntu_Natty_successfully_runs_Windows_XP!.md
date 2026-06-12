---
title: "Kubuntu Natty successfully runs Windows XP!"
date: 2011-06-27
forum: General Help
---

### Post by jamadagni on 2011-06-27
@moderators: I intentionally post this here in the general thread instead of the specific virtualization sub-forum because I thought it would be good for the average user (who is more likely to visit here than there) to know that this is possible. I hope this is OK.

I recently bought an IdeaPad Z570 laptop with Sandy Bridge Intel Core i5 processor, 3 GB RAM etc.

I still have things that I am forced to go to Windows for, so I had to make it a dual boot system. And I went and installed Windows 7 because that's what Lenovo provides the drivers for.

But to my dismay, lots of stuff, especially my Keyman keyboards, didn't work on Windows 7. So I installed Windows XP!

But there are no drivers for this latest hardware for Windows XP. So what did I do?

Installed VirtualBox on Kubuntu and installed Windows XP as a guest system using it! :D Linux/Kubuntu takes care of the hardware (or something like that).

Installing VirtualBox Guest Addons from Multiverse also enables me to share directories between the Linux host and Windows guest, so I can access the files on my Windows D drive by mounting it in Linux (which I do by default in /etc/fstab anyway) and sharing it via VirtualBox Shared Folders.

Given that Intel Virtualization Acceleration technology is inbuilt into the new processor/chipset, I don't feel much difference in speed! :)

Just posting it here in the hope that it catches somebody's imagination. For discussion and support please go the [virtualization sub-forum](http://ubuntuforums.org/forumdisplay.php?f=308).

---

### Post by Beacon11 on 2011-06-27
Just FYI: Linux doesn't have anything to do with the hardware for XP-- that's all handled by VirtualBox (indeed, that's its purpose).

---

