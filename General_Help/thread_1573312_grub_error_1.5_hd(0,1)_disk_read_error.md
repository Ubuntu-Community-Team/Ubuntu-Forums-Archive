---
title: "grub error 1.5 hd(0,1) disk read error"
date: 2010-09-12
forum: General Help
---

### Post by Nsmith0723 on 2010-09-12
Ok. So my hard drive crashed. (i was running Linux 10.4)so i put in another hard drive, installed Ubuntu 10.4, and on boot up i get that error. I've tried reinstalling it with the server edition. different hard drives. all I get is that message. I've read other posts similar, but nothing helped. plz help.

---

### Post by Lukas666 on 2010-09-12
How is the drive partitioned?

---

### Post by Nsmith0723 on 2010-09-12
normally i guess. 160g. 156.2g Ubuntu's file system and the lot. 3.8 swap. there are no other hard drives.

---

### Post by Lukas666 on 2010-09-12
Did you try to boot from CD and update grub from there?

---

### Post by Nsmith0723 on 2010-09-12
O. i didn't know you could

---

### Post by Lukas666 on 2010-09-12
> **Nsmith0723 said:**
> O. i didn't know you could

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

SKIP THE STEP "C" [GRUB installation] since you already have it.

---

### Post by Nsmith0723 on 2010-09-12
OK. ill will try this. thanks. I'll post when i'm finished and mark this thread accordingly.

---

### Post by Nsmith0723 on 2010-09-12
Nope. i still get the disk read error.

---

### Post by Lukas666 on 2010-09-12
> **Nsmith0723 said:**
> Nope. i still get the disk read error.

Could you connect it to a different computer using a USB cable? Just to make sure the drive works.

---

### Post by Nsmith0723 on 2010-09-12
I know is not the drive. I've tried this on another hard drive two. idk maybe my mother board fried when the hard drive crashed. idk

---

### Post by Lukas666 on 2010-09-12
> **Nsmith0723 said:**
> I know is not the drive. I've tried this on another hard drive two. idk maybe my mother board fried when the hard drive crashed. idk

Maybe you could try to reinstall grub?

---

### Post by Nsmith0723 on 2010-09-12
I've got it working. I belive theres something wrong with the IDE when the hard drive crashed. usb flash drive works fine. I have a small hard drive on the machine. is there any way to store program files on that hard drive?

---

