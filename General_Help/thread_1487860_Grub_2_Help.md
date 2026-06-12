---
title: "Grub 2 Help"
date: 2010-05-19
forum: General Help
---

### Post by carguy303 on 2010-05-19
I have recently upgraded to grub 2 from grub legacy and I am having a bit of trouble of readjusting to grub 2. From other posts I found out how to adjust the timeout. When I followed another post that showed me how to adjust the title I rebooted and ubuntu and the recovery appeared twice with none of the adjustments I made. please help

---

### Post by mikewhatever on 2010-05-19
Usually, you'll get as many Ubuntu entries as there are kernels installed. That means a new entry gets added after every kernel update, which is normal behavior. You can remove the old kernel versions from time to time to reclaim some disk space and unclutter the grub menu.
As for adjusting various grub settings, don't forget to run *sudo update-grub* for the changes to take effect.

---

### Post by Catharsis on 2010-05-19
This might help:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

