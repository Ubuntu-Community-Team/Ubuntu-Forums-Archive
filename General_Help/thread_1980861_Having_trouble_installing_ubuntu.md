---
title: "Having trouble installing ubuntu"
date: 2012-05-15
forum: General Help
---

### Post by Ranzar on 2012-05-15
When booting from a live cd I get:
" ata_id[369]: hdio_get_identity failed for '/dev/sdc': invalid argument "
I tried 2 different burned live cd's and got the message and I even tried the method of installing via windows and got the same error. I'm having a hard time googling for answers, does anybody know how to solve this error? I'd like to mention that installing via Windows installed some of Ubuntu but it will not boot.

---

### Post by Rodney9 on 2012-05-15
Try running the installation with

```
nomodeset
```

when the install is starting up, press Esc and then go to more options and press Enter and select nomodeset. That should let you boot.

Rodney

---

