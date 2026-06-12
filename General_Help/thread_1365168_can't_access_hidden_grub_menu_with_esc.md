---
title: "can't access hidden grub menu with esc"
date: 2009-12-26
forum: General Help
---

### Post by ghettosamson on 2009-12-26
I am running Hardy Heron. I edited the menu.lst file to default to what I thought was Windows XP instead of Ubuntu, counting from 0 and set the timeout to 0. Now it automatically goes into the memtest and I cant load any of my OS's. When I press esc it won't show the hidden grub menu and I tried alt esc I tried shift and a bunch of other key combinations but nothing has worked. Can anyone help?

---

### Post by taurus on 2009-12-26
If you cannot get into GRUB menu, then you need to boot your machine with the LiveCD.  Then mount the partition where /boot is, and edit /boot/grub/menu.lst.  Change the timeout to some integer.

---

### Post by Mahngiel on 2009-12-26
yep. live cd.

---

### Post by angry_johnnie on 2009-12-26
press and hold the shift button instead of esc.  it will show your hidden menu.

---

### Post by taurus on 2009-12-26
> **angry_johnnie said:**
> press and hold the shift button instead of esc.  it will show your hidden menu.

Isn't the shift key only for Grub2 (/etc/default/grub) while Hardy is still using the old version of Grub (/boot/grub/menu.lst)?

---

### Post by Mahngiel on 2009-12-26
> **taurus said:**
> Isn't the shift key only for Grub2 (/etc/default/grub) while Hardy is still using the old version of Grub (/boot/grub/menu.lst)?

quite positively correct, sir.  :KS

---

### Post by ghettosamson on 2009-12-28
> **taurus said:**
> If you cannot get into GRUB menu, then you need to boot your machine with the LiveCD.  Then mount the partition where /boot is, and edit /boot/grub/menu.lst.  Change the timeout to some integer.

I mounted the partition but when I opened the file it opens in read only mode so I am not able to modify the file. Is there a workaround?

---

### Post by angry_johnnie on 2009-12-28
to modify a read-only file:

in terminal
```

cd /your-drive/boot/grub
sudo chmod a+w menu.lst
gksu gedit menu.lst
```

change it & save it

---

### Post by ghettosamson on 2009-12-28
> **angry_johnnie said:**
> to modify a read-only file:

in terminal
```

cd /your-drive/boot/grub
sudo chmod a+w menu.lst
gksu gedit menu.lst
```

change it & save it

Thanks! Cheers!

---

