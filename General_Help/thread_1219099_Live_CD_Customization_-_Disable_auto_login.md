---
title: "Live CD Customization - Disable auto login"
date: 2009-07-21
forum: General Help
---

### Post by sebz on 2009-07-21
Hello,

I currently doing the Live CD Customization ([https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)).


I have an issue here. I need to disable the autologin from the Live CD user (ubuntu).

But when I do the chroot to edit the Live CD ISO image, I can't access the System Tabs and go to the user account (I only have access to the Terminal).

My question is; where is the config file to disable the auto login from my Live CD?

If you need more information, please let me know. :D

Thanks!

---

### Post by jerrrys on 2009-07-22
don't know if this will help, but in terminal   **gksu /usr/sbin/gdmsetup**

---

### Post by Bladehawke on 2009-08-08
Edit or remove /usr/share/initramfs-tools/scripts/casper-bottom/15autologin then regenerate your initramfs

---

