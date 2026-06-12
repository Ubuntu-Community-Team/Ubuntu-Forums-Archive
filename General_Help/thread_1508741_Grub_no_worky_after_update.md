---
title: "Grub no worky after update"
date: 2010-06-13
forum: General Help
---

### Post by jblaine271 on 2010-06-13
Hey guys,

So, when I go to boot Ubuntu, my screen flashes


Try (hd0, 0) NTFS

Then immediately goes back to my HP boot up screen... any idea what's going on?

---

### Post by Monotoko on 2010-06-13
Try booting from a LiveCD then use:

```
sudo update-grub
```


Dan

---

### Post by oldfred on 2010-06-13
Since it mentions NTFS was this a wubi install inside the windows partition. Then did you install grub to the MBR, but wubi uses the windows boot loader in the MBR.

To see you configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

