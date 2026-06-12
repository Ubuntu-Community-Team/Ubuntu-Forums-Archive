---
title: "Downgrade Kernel?"
date: 2010-03-07
forum: General Help
---

### Post by gcndavidmn on 2010-03-07
It looks like the latest kernel update has borked the sound on my Macbook Pro 5 4. Is it possible to downgrade to the previous version (which i believe is -19) where my sound worked? If so, how do I go about this?

Regards
Dave

---

### Post by patchwork on 2010-03-07
There are a couple of different ways to go about this.

You can remove the kernel (assuming you have another kernel to boot) through Synaptic, or you can change the default kernel in your /etc/default/grub by either specifying a number (menu entries count from 0) or the word 'saved'.
If you choose to go the 'saved' route, you will need to enter the command ```
sudo grub-set-default #
``` where # is the number of the entry (again, counts from 0).

Any method you choose, you will need to update your grub:
```
sudo update-grub
```

---

### Post by gcndavidmn on 2010-03-07
I just checked my GRUB on startup and I have -20 and -14. I have tried booting into -14 (what I presume was installed by default) but it says something about my graphics settings/hardware and all of the options just lead to errors. What do I do?

---

