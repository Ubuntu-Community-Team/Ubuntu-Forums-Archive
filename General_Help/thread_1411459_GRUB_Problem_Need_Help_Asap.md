---
title: "GRUB Problem Need Help Asap"
date: 2010-02-20
forum: General Help
---

### Post by spacelad101 on 2010-02-20
ok, i was screwing with some of the settings that have to do with my hard drive on Ubuntu 9.10, and i change a setting (I forget which one now) to something that has to do with mac os boot. not thinking much of it when i did it i forgot to put it back to its default which was a linux boot and then i turned off my computer. Now i keep getting this error when i turn on my computer "GRUB loading, please wait... Error 15." I have tried re-installing ubuntu, i have tried to install kubuntu and everything seems to lead back to GRUB. Please help, i have no idea what to do, and if you do decide to help me, please give me as much detail as possible on how to solve this, im not exactly all knowing about computers.

---

### Post by NightwishFan on 2010-02-20
Here is another thread about Grub Error 15:
[http://ubuntuforums.org/showthread.php?t=892301](http://ubuntuforums.org/showthread.php?t=892301)

---

### Post by amsterdamharu on 2010-02-20
Assuming you have grub2 (ubuntu 9.10) and an ubuntu 9.10 CD to boot from you can try this:

The live cd option is the top option when booting from the cd something like "try ubuntu"

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That tutorial should mention when using grub2 you have to run the following command after installing grub2 and before rebooting:
```

sudo update-grub2
```

---

### Post by spacelad101 on 2010-02-20
im not running grub 2, i had 9.04 installed then i upgraded to 9.10 and according to the forum link, im running grub legacy. Does it make a difference?

---

### Post by spacelad101 on 2010-02-20
THANKYOU!!!!! I just fixed it thank-you sooooo much =)

---

