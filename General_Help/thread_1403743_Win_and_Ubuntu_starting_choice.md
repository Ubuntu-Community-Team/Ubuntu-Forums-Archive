---
title: "Win and Ubuntu starting choice"
date: 2010-02-10
forum: General Help
---

### Post by johnheating on 2010-02-10
After unistalling Ubuntu from the PC, left me with the choice to start Windows or Ubuntu.
How can I remove this option please? I don't have anything against Ubuntu, just I find it too much having to learn new jargon after 30 years with Win. Your help is appreciated. Thanks.

---

### Post by Overcast32 on 2010-02-10
> **johnheating said:**
> After unistalling Ubuntu from the PC, left me with the choice to start Windows or Ubuntu.
How can I remove this option please? I don't have anything against Ubuntu, just I find it too much having to learn new jargon after 30 years with Win. Your help is appreciated. Thanks.

I'm guessing that's the Grub boot loader still there - but Linux partitions gone?

Check this page, it might help

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")

If it was me, rather than dig too deep and start messing with partitions, I'd just make sure Windows is the default and change the timeout to 0 (or maybe 5 personally) so it's basically done immediately.

---

### Post by johnheating on 2010-02-11
Thank you for the reply. Yes I've reduced the wait to 3sec Thats the min allowed. Thanks again. Regards

---

### Post by giammy on 2010-02-11
> **johnheating said:**
> After unistalling Ubuntu from the PC, left me with the choice to start Windows or Ubuntu.
How can I remove this option please? I don't have anything against Ubuntu, just I find it too much having to learn new jargon after 30 years with Win. Your help is appreciated. Thanks.

Hi,

usually Grub boot loader is installed in the master boot sector:
once upon a time (Windows 98) when I was  testing with linux
I used "fdisk /mbr" (which on W98 deleted the master boot record
and grub.

WARNING: this worked on W98: I do not know if it works now - you
                 should hear from a Windows expert

---

### Post by Swagman on 2010-02-11
Did he dual boot or use wubi ?

---

### Post by Andreas1 on 2010-02-11
> **giammy said:**
> Hi,

usually Grub boot loader is installed in the master boot sector:
once upon a time (Windows 98) when I was  testing with linux
I used "fdisk /mbr" (which on W98 deleted the master boot record
and grub.

WARNING: this worked on W98: I do not know if it works now - you
                 should hear from a Windows expert

with windows xp this still works. boot winxp setup cd, press R to start recovery console, enter "fixmbr" to rewrite master boot record.

---

