---
title: "Spash screen display problems"
date: 2010-04-29
forum: General Help
---

### Post by warden976 on 2010-04-29
hi all,

upgraded from 9.10 64bit to 10.04 64bit, generally it's all gone well, however the purple ubuntu splash screen is displaying at a very low resolution making it look terrible, but when i boot from the live CD the splash screen is displayed at the correct resolution and looks good...

how can i fix this?

cheers

---

### Post by trevelyan on 2010-04-29
i also have this problem. it happened after i installed the nvidia proprietary drivers using the "hardware drivers" tool. i installed the current version of the drivers. i'm still looking for a solution but havent been able to find one so far.

---

### Post by trevelyan on 2010-04-29
got it! here is what i did:

```

sudo nano /etc/default/grub

```
edit this line with your native resolution. mine is 1680x1050, also make sure you delete the # at the beginning.
```

#GRUB_GFXMODE=640x480

```

after you've done that run:
```

sudo update-grub2

```

hope that helps.

---

### Post by warden976 on 2010-04-30
i tried that but am afraid it didn't work for me...

i've got an acer aspire with using the proprietary ATI/AMD FGLRX driver. i did uninstall this to test it and the splash screen still display at a much too low resolution...

---

