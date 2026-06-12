---
title: "Ubuntu boot timer"
date: 2010-01-31
forum: General Help
---

### Post by schwabdale on 2010-01-31
I installed Ubuntu with windows. Can someone tell me how to change the boot timer from 10 seconds to 3?

Thanks

---

### Post by Leppie on 2010-01-31
if you're using grub2 (karmic ships with grub2 and i believe i saw in another thread you installed karmic):
open your grub defaults file with your text editor:
```
gksudo gedit /etc/default/grub
```change the timeout line like this:
```
GRUB_TIMEOUT="3"
```save and exit the file. then run update-grub:
```
sudo update-grub
```grub2 should now automatically boot into your default system after 3 seconds.

---

