---
title: "Why does ubuntu makes automatic disk check at startup?"
date: 2011-11-19
forum: General Help
---

### Post by arroy_0209 on 2011-11-19
I am using ubuntu 10.04 LTS. I notice the OS makes an automatic disk check at startup sometimes (messages like "your disk drive is being checked...disk 1 of ... is checked" appear.) What does that mean? Is my drive having any problem which makes ubuntu suspicious? 

Is there any way to know if there is any problem with the disk in my machine so that I can be cautious and take backup frequently?

---

### Post by Elfy on 2011-11-19
> Is my drive having any problem which makes ubuntu suspicious? No - it is set in fstab to check the drive at intervals.

> Is there any way to know if there is any problem with the disk in my machine Disk utility accesses smart data.

> so that I can be cautious and take backup frequently?You should be doing that before you get a problem ;)

---

### Post by papibe on 2011-11-19
It is a common practice. Every certain number of boots the system will check the disks for errors and repair them if they exist.

There is a tool so you can check your disk in case you feel uneasy. It's in System -> Administration -> Disk Utility. You can select your disk and partition and check it by pressing the option 'Check Filesystem'.

Hope it helps,
Regards.

EDIT: forestpiskie was faster!

---

