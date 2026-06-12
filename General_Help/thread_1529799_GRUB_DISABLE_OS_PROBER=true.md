---
title: "GRUB_DISABLE_OS_PROBER=true"
date: 2010-07-12
forum: General Help
---

### Post by MountainX on 2010-07-12
What is the resulting grub.cfg file supposed to look like after including the code below in /etc/default/grub?

```
GRUB_DISABLE_OS_PROBER=true
```

I also tried setting it equal to "true" (vs true without quotes). In either case, the OS prober section appears in grub.cfg.

What would happen if I just manually delete that section?

---

### Post by Leppie on 2010-07-12
it would be easier to issue the following command:
```
sudo chmod a-x /etc/grub.d/30_os-prober
```

---

### Post by MountainX on 2010-07-12
> **Leppie said:**
> it would be easier to issue the following command:
```
sudo chmod a-x /etc/grub.d/30_os-prober
```

OK, so you are telling me that when this is done correctly the whole 30* section should just be absent from grub.cfg. Right???

Your way seems effective, but obviously that wasn't the intent of the grub2 developers any more than it was for me to edit grub.cfg manually. It would be nice to know how it is supposed to work.

Anyway, for now, I'll just manually delete section 30* from grub.cfg.

I see why so many people are complaining about grub2...

---

### Post by Leppie on 2010-07-12
the aforementioned command basically does the same as the 
GRUB_DISABLE_OS_PROBER=true option in the grub defaults file.
using the command will permanently disable the os prober, so you do not have to modify your grub.cfg every time update-grub is run.

---

### Post by MountainX on 2010-07-12
> **Leppie said:**
> the aforementioned command basically does the same as the 
GRUB_DISABLE_OS_PROBER=true option in the grub defaults file.
using the command will permanently disable the os prober, so you do not have to modify your grub.cfg every time update-grub is run.

OK, thanks. My method doesn't seem to work as desired. It makes the grub menu appear, which I didn't want.

---

### Post by Leppie on 2010-07-12
in the end, you could edit the grub.cfg every time update-grub is run. but why would you do that if it isn't necessary since there's other ways to make it stick? would be kind of masochistic, don't you think?

anyways, if you really do want to edit the grub.cfg, you should delete the piece between the 30_os-prober comments (start and end), but don't remove the comments themselves.

---

### Post by drs305 on 2010-07-13
Per the OP request, the thread was split at this point as the discussion turned to Grub 2's use of labels. 

That thread is now located here:
[http://ubuntuforums.org/showthread.php?t=1530532]("http://ubuntuforums.org/showthread.php?t=1530532")

---

