---
title: "Shell problem ??"
date: 2011-06-09
forum: General Help
---

### Post by muppy80 on 2011-06-09
Hi All,
i'm pretty new to ubuntu. I was "playing" trying to change my default shell and failed.
Now, after logging in, i open a terminal window and type "su". Ubuntu asks me a password, i give my password and i get this error "unable to execture /bin/bsd-csh: file or directory does not exist".

Any idea on how to solve this problem restoring my old shell ??

Thanks,
Andrea

---

### Post by sisco311 on 2011-06-09
With su you start a root shell, so I think you changed root's default shell. In order to change it back, you have to run:
```
sudo chsh -s /bin/bash root
```

If you want to change your user's shell, simply run:
```
chsh
```

---

### Post by muppy80 on 2011-06-11
Ok, i solved thanks to your suggestion and to this thread

[http://ubuntuforums.org/showthread.php?t=1702833](http://ubuntuforums.org/showthread.php?t=1702833)

Thanks!!
Andrea

---

