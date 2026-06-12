---
title: "my ubuntu had disappered ! help"
date: 2009-10-04
forum: General Help
---

### Post by drwolf on 2009-10-04
I used to have dual booting system including ubuntu 8.10 and windows 7 CR however i installed windows 7 RTM today ...now the system boot into win7 immadiatly without list of options what should i do to resecue my lost ubuntu ? help me PLZ

---

### Post by ermeyers on 2009-10-04
I think it's gone.  Try booting an Ubuntu Live CD, to see if anything Ubuntu is left on the disks.

---

### Post by DGortze380 on 2009-10-04
Windows overwrites your boot loader.
You'll need to reinstall grub.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by drwolf on 2009-10-04
but every system was in a different patition and when i installed win 7 rtm i selected to be installed on the cr partition ..

---

### Post by ermeyers on 2009-10-04
grub typically goes into the Master Boot Record (MBR) of the first partition.

sudo grub-install hd0

---

### Post by filipvermeiren on 2009-10-04
does not matter, windows still over writes your Master Boot Record.

---

### Post by drwolf on 2009-10-04
i get this :
could not find device for /boot : not found or not a block device

---

### Post by DGortze380 on 2009-10-04
> **drwolf said:**
> i get this :
could not find device for /boot : not found or not a block device

When do you 'get this'. be more specific please.

---

### Post by JC Cheloven on 2009-10-04
Plz trust us: your ubuntu is surely here. Only windoze has broken your boot setup (whatever it means, don't worry about the details, mbr, etc; too long to explain in a help post). Your options are: 

1) Follow Dgortze's advice. This involves restoring your previous boot setup based on free software, and adding manually an entry for the newly installed OS. The link he gave you is ok for that.
2) Use SuperGrubDisk, which somehow eases the process. It also installs the free software bootloader (which as you're seeing is much more capable than the proprietary one).

---

