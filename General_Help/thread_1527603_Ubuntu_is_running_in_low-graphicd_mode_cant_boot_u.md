---
title: "Ubuntu is running in low-graphicd mode cant boot up"
date: 2010-07-09
forum: General Help
---

### Post by Sveinbjorn on 2010-07-09
My girlfriend accidentally removed the power from the computer and now i cant boot up. I just get Ubuntu is running in low-graphics mode and than:
0 run ubuntu in low-graphics mode for just one session
0 reconfigure graphics
0 troubleshoot error
0 exit to console
0 restart x
the only thing im able to do is boot up in terminal mode.
i have tried google and found nothing that worked.
thanks :)

---

### Post by cariboo on 2010-07-09
Boot from the Live CD and run fsck on your partition. Open a terminal once you are at the desktop and type:

```
sudo fsck -a /dev/sda1
```

substitute your partition for the one in the example above.

---

