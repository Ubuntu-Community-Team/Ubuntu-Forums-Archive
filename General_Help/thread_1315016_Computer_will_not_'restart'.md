---
title: "Computer will not 'restart'"
date: 2009-11-04
forum: General Help
---

### Post by HeretikSaint on 2009-11-04
I'm currently using Ubuntu 9.10 but the problem has been occuring since the previous version (9.04) as well.  I will hit the 'Restart' button from my menu or even after a major upgrade and Ubuntu will shut down and I will get a message like:
```

[49203.59203947] Restarting system...
```
but the system never restarts.  (Note: The numbers in the code section were just randomly typed.  I haven't actually written them down or noticed if they are a specific, reoccurring number.)  I'm not sure if this is an Ubuntu or a Grub issue.  Any and all help is appreciated.  Let me know if you require any more specific information.

---

### Post by x C0MMAND0 x on 2009-11-04
Try running

```
sudo shutdown -r now
```

Any seeing if that works...

---

### Post by HeretikSaint on 2009-11-05
> **x C0MMAND0 x said:**
> Try running

```
sudo shutdown -r now
```

Any seeing if that works...

Yes, that worked.  Any idea why that works and using the 'Restart' option from the top menu wouldn't?

---

### Post by x C0MMAND0 x on 2009-11-05
If you click on "System > Shut Down", and then click restart from there does it work?  Or is that bringing you to the same "Shutdown" menu that the one you currently use does?

---

