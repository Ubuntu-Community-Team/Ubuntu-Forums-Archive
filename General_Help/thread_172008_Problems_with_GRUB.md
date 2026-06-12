---
title: "Problems with GRUB"
date: 2006-05-07
forum: General Help
---

### Post by Aljo on 2006-05-07
I recently reinstalled windows onto a blank partition on a hd that already had Ubuntu on it, and now my computer doesn't load GRUB on startup. Is there anyway to fix this without reinstalling Ubuntu?

---

### Post by Herman on 2006-05-07
[B][http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")
Re-install GRUB[/B]
    If you have re-installed Windows, or installed Windows after Ubuntu instead of first,  Windows will write it's own 'bootsector' back on your MBR, pointing to it's own 'boot.ini' file, erasing GRUB's 'stage 1'. You'll need to re-install GRUB, in order to provide you the option to boot Ubuntu. There are numerous ways to re-install stage1 of GRUB to your MBR, and make it point to your Ubuntu  /boot directory again. Choose any of the methods you like described in these links below:
     
    From the Official Ubuntu Wiki: [Re-installing GRUB]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29")  see also:   |     [  Swiss2K thread]("http://www.ubuntuforums.org/showthread.php?t=114332")    |    [Arnieboy thread]("http://ubuntuforums.org/showthread.php?t=76652")    |    [vnbuddy2002 thread]("http://www.ubuntuforums.org/showthread.php?t=24113")

Hello, Aljo, I just copied the above from my GRUB web-page for you. That should be more than enough to answer your question, and if you gt time, there's more there you can read as well if you want. :D Good luck with it, Regards, Herman

---

### Post by halitech on 2006-05-07
check here:

[GRUB Recovery]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28mbr%29")

Windows doesn't like to play nice so you will have to redo GRUB

---

