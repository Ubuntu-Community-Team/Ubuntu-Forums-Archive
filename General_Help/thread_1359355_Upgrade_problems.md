---
title: "Upgrade problems"
date: 2009-12-19
forum: General Help
---

### Post by njp94 on 2009-12-19
I am running Ubuntu 9.04 on a Dell Latitude C840 laptop computer. The fdisk -l commnad gives the following result
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022c50

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7110    57111043+  83  Linux
/dev/sda2            7111        7296     1494045    5  Extended
/dev/sda5            7111        7296     1494013+  82  Linux swap / Solaris

After running the Update manager with the recent upgrades, the system has been corrupted and I am not able to boot from hard desk any longer. The boot process stops in the first part of the sequence independent of which Linux version I use. 
Is there an easy way to recover the system without having to reinstall the system from the beginning and delete all files in my /home directory_

---

### Post by HappyFeet on 2009-12-19
> **njp94 said:**
> 
Is there an easy way to recover the system without having to reinstall the system from the beginning and delete all files in my /home directory_

There is no reason to lose the contents of your home folder if you need to reinstall. Just use a live cd to recover them, and save whatever you want to an external drive, or pendrive. When in your home folder, do **Ctrl-H** to show the hidden configuration files. Then you can cherry pick which ones you want to save.

If this is not satisfactory to you, I hope someone else will be able to help you more. Good luck.

---

### Post by njp94 on 2009-12-19
Thank you for your proposal. A reinstallation of Ubuntu 9.04 with a backup of my /home directory is one of my options, but I thought, than when I can boot from a live CD, I can get Ubuntu 9.04 up running and I can get access to all my files at the harddisk, I could also make a resinstallation of the system files without deleting any files in my /home directory. One problem is also that I do not have any backup mediums that have enough capacity for all the files /home.

---

