---
title: "change default boot OS"
date: 2010-02-11
forum: General Help
---

### Post by melhxi on 2010-02-11
[SIZE=3]What's newer than new?  I just (an hour ago) loaded Ubuntu 9.10 onto my Vista Home Edition PC.  It's my very first try at using any kind of Linux.  Ubuntu loaded great, and I have booted to it (it's now the default OS) and into Vista (by arrowing down on the new boot menu).  All was well but......

I wanted the PC to start in windows for the sake of my wife and the other users of the PC.  I looked up the steps to edit the menu.1st file to change the "0" boot number to "4", BUT....

As soon as I enter my Ubuntu password, on the command line,  the command line returns with words to the effect that there is no such file as menu.1st to edit.  And yet, when I do a PC restart, there's the menu listing the boot alternatives again.

Please help.  If I leave the PC with my co-users needing to arrow down to Vista within the menu's time limit, I'll get moidered.
[/SIZE]

---

### Post by flippo on 2010-02-11
Message was incorrect, please see following posts.

---

### Post by NightwishFan on 2010-02-11
You need the Grub2 tutorial if you have Grub2. If you have grub1, the above should work.
[https://wiki.ubuntu.com/Grub2#Grub%202%20Files%20&%20Folders](https://wiki.ubuntu.com/Grub2#Grub%202%20Files%20&%20Folders)

---

### Post by audiomick on 2010-02-11
Hi.
You wont find menu.list on a fresh 9.10 install. The boot loader has been changed to the newer grub 2
There are instructions here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by flippo on 2010-02-11
Sorry, they are both correct.  I apparently need to catch up with all the new packages in the newer versions.

---

### Post by melhxi on 2010-02-11
[SIZE=5]Thanks everyone.  I'm off to try the new version edit.  I would have been fussing around for hours without your help.


[/SIZE]

---

