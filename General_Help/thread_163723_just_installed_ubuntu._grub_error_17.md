---
title: "just installed ubuntu. grub error 17"
date: 2006-04-21
forum: General Help
---

### Post by cosmoshell on 2006-04-21
i installed ubuntu on a freinds computer and im getting "grub loading stage 1.5 grubloading, please wait... eror 17. can someone help me

---

### Post by Kenosis on 2006-04-21
Had this too, try re-installing Grub:

1. Boot onto liveCD
2. Open Terminal and Type:
3. sudo su
4. mkdir /ubuntu
5. mount /dev/hd(location of your ubuntu root partition) /ubuntu
6. chroot /ubuntu /bin/bash
7. grub
8. root (hd0,0) [change number to match "hardrive,partition"]
9.setup (hd0) [again, change if your ubuntu HDD is not /dev/hda]
10. quit
11. reboot

For more explanation, go here: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

Otherwise, just re-install that baby...which is what I am currently doing.

- Good Luck!


Dell Latitude D600 Laptop w/40GB HDD

- Kenosis

---

### Post by cosmoshell on 2006-04-21
ive already reinstalled it a few time with no luck but ill try reinstallin grub.

thanks for the advice

---

