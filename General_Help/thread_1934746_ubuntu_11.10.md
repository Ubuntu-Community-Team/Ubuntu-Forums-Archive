---
title: "ubuntu 11.10"
date: 2012-03-02
forum: General Help
---

### Post by greenman55 on 2012-03-02
hey, so i have a new hard drive and i decided to install ubuntu 11.10 on it and my other harddrive has ubuntu 10.04 lts and lts works great but 11.10 isnot what imlooking for :( . then i found out i need windows xp for my work that im doing. i went to cmos and made it boot from cd and incerted my xp disk then when it starts up it says "press any key to boot from cd" i pressed some keys and nothing it just went to ubuntu 11.10, i tryed to install it on my desktop but it wont alow me to mark as executable :confused: please help. im very new to ubuntu. any help is very appreciated!

---

### Post by QIII on 2012-03-02
To avoid a frustrating mistake, unplug your 10.04 disk.

Use one of your ubuntu LiveCDs and format the remaining drive as NTFS.  Log out of Live session, remove the CD and shut down.  Restart with the XP CD in the drive.  Install XP.

When XP is installed, shut down again.  Plug your Ubuntu drive back in.  Start up and go to your BIOS.  Set the Ubuntu drive first in your hdd boot order.

Allow the machine to start up, which should bring you to Ubuntu.

In the terminal

```
sudo update-grub
```

If you shut down and restart, you should see both Ubuntu and XP as selections.

---

