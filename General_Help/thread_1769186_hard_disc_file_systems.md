---
title: "hard disc file systems"
date: 2011-05-27
forum: General Help
---

### Post by soulcat on 2011-05-27
hi

 hi why is it when i go in to my back up hard drive or various hard drive file systems it leaves icons on the desktop bit like a paper trail, then when i reboot they clear.....can i stop this from littering my desktop


 ubuntu 10.10

---

### Post by doas777 on 2011-05-27
I'm completely confused as to what you are describing, but some applications that perform operations on disks as a whole, will generate many temporary files to "spool" the data too as a output buffer. when the application is finished, these files are usually deleted but can remain if the application was aborted.

somthing is likely not working as intended based on your description. could you post an image?

---

### Post by soulcat on 2011-05-27
hi

attachment shows backup file systems as i enter them on my desktop as described like a paper trail...just want to know why bit annoying

---

### Post by doas777 on 2011-05-27
do you mean the HardDisk/Volume icons?

gnome will often display icons for mounted volumes, so if you don't usually mount your hdds at boot, the backup software may be doing so for you, so that it can backup the volume. thats when the icon shows up.
these drives will unmount themselves at shutdown, so if you rebooted, they would disappear, until someone or some app mounts them again. that kind of sounds like what you are describing.

this link will show you how to keep gnome from showing the volume shortcut when the drive is mounted. that way you dont have to look at them.
[http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/](http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/)

---

### Post by soulcat on 2011-05-27
thanx for your reply, using ubuntu now for about month or so now still getting to grips with a few little niggles

regards

---

### Post by soulcat on 2011-05-27
worked a treat cheers

regards):P

---

