---
title: "Access to windows folders"
date: 2010-10-31
forum: General Help
---

### Post by Ironic on 2010-10-31
I have installed ubuntu in dual boot in XP

 Now i would like to be able to quickly access folders on XP partition, maybe with shortcuts on desktop?

 However if i create those shortcuts and restart computer the shortcuts are no longer valid.

Any way around this, or is there a better way to reach XP partition folders without going to root of drive every time?

Thank You

---

### Post by coffeecat on 2010-10-31
If you arrange your /etc/fstab to mount your Windows XP partition on bootup, then your desktop shortcuts will work and you won't have to navigate from the root of the XP filesystem. However, having a Windows C: drive permanently mounted read-write is not a good idea. XP seems more tolerant than Vista and 7, but strange things can happen if you write to a C: drive from outside of Windows. Best to mount for reading only and unmount as necessary.

What most people do is to have a separate NTFS shared data drive which Windows will see as D:/E: or whatever. Mounted from fstab for Ubuntu, that is safer. That's what I do on my two laptops.

Guide to /etc/fstab:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Ironic on 2010-10-31
The files i want to access are located in D: , so i will look into that.

Thank You

---

