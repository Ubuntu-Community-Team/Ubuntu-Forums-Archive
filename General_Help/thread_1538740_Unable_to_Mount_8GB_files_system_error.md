---
title: "Unable to Mount 8GB files system error"
date: 2010-07-25
forum: General Help
---

### Post by cozski on 2010-07-25
Compact Flash card cant be read... the error says 'not authorised'. I'm using a mutli-card reader. Do I have to do something else? It reads my SD card in the same reader no problem.

Thanks

---

### Post by Vishnu V on 2010-07-26
Try to mount it manually
```

sudo su
mkdir /media/card
mount /dev/sdaX /media/card

```
where X is a number and you can find it using
```

sudo fdisk -l

```

---

### Post by cozski on 2010-07-26
Thanks, but I just inserted the CF card and it mounted seamlessly... but thanks for the advice... much appreciated.

---

