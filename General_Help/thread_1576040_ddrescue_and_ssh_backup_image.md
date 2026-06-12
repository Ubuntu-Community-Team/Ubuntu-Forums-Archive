---
title: "ddrescue and ssh backup image"
date: 2010-09-16
forum: General Help
---

### Post by supre on 2010-09-16
hi there,

im trying to use ddrescue to clone a dying disk to a remote machine using ssh. this is my command:
> sudo ddrescue --block-size=4KiB /dev/sda1 - | ssh user@address 'cat /data/backup.img'
i've googled and googled, but the googles, they do nothing. it returns the error "cat: can't open '/data/backup.img': No such file or directory"

but i cant see why

---

### Post by Baked- on 2010-09-16
try
ddrescue /dev/sda1 sda1.img | scp sda1.img user@host:~

not sure what options you need for ddrescue but as far as xfering the file that should work

---

### Post by supre on 2010-09-16
i dont have any local disk to keep the image on though while it transfers. would that go on the fly?

---

### Post by Baked- on 2010-09-16
no it wouldnt sorry, didnt think about that.

---

