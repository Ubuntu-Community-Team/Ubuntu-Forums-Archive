---
title: "expand install from dual boot setup"
date: 2009-07-03
forum: General Help
---

### Post by factotum218 on 2009-07-03
Awesome, just awesome.

I finally have 9.04 amd64 up and running without a hang up. Even Virtualbox OSE with xp for InDesign. Everything all set up the way I want it, which is why I have a question.

Right now it's a dual boot with Vista. 250gb drive split in half on a laptop. Is there a way to remove the Vista ntfs (don't need to back up anything off of it), move the / and swap and expand the /home to fill the drive?

So far I've only excluded the vista selection in GRUB.

Thanks a million!

---

### Post by merlinus on 2009-07-03
Post results of

```
sudo fdisk -l
```

Another idea would be to format your existing windows partition as ext3. mount it as /data, and use it for storing same.

---

