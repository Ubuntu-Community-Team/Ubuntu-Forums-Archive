---
title: "Stuck with wrong GRUB: Mount of root filesystem failed"
date: 2010-05-23
forum: General Help
---

### Post by Zilioum on 2010-05-23
A friend of mine upgraded his pc to ubuntu 10.04. Sadly enough we ran into issues with his graphics card, which apparently doesnt work well with lucid. We decided to downgrade to 9.10. I did this by installing over the old partition and chose to import the settings from the old account.
The problems started when the pc booted for the first time:
The list of kernels in grub2 was the one from 10.04.
We then got > mountpoint /dev/shm does not exist and > Mount of root filesystem failed.
This is very weird, because dev/shm does indeed not exist, I have no idea where this is from.
I used the live cd to try to fix it:
```
sudo update-grub
``` gives me ```
grub-probe: error: cannot find a device for /.
```
reinstalling grub2 as described in the official documentation didnt change things either.
```
sudo fdisk -l
``` does work: ```
   
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24330   195430693+  83  Linux
/dev/sda2           24331       29455    41166562+   7  HPFS/NTFS
/dev/sda3           29456       30401     7598745    5  Extended
/dev/sda5           29456       30401     7598713+  82  Linux swap / Solaris

```

but the fstab file looks very wrong:
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

Somehow grub2 from the old installation seems to be still around and messes everything up. Any ideas how I could fix this?

Cheers

---

### Post by mikewhatever on 2010-05-23
Why do you think grub2 from Lucid installation is still there? It shouldn't be, since you installed Karmic over. Yet, somehow, that installation didn't go well, as there is no root file system in fstab.

---

### Post by Zilioum on 2010-05-23
> Why do you think grub2 from Lucid installation is still there? Because the list of kernels is the one from lucid and the entry for Windows XP is still there as well. If grub2 was "new" this entry should be gone.
 > as there is no root file system in fstab
I think this is the main problem. How can I fix that?

Cheers

---

### Post by mikewhatever on 2010-05-23
Try reinstalling. Perhaps it works better this time.

---

### Post by Zilioum on 2010-05-23
Reinstall grub or ubuntu? Reinstalling ubuntu should resolve the problem, but I'd prefer to fix the version currently installed. 
Any ideas how I could fix the fstab for example?

Cheers

---

### Post by mikewhatever on 2010-05-23
You should probably go with a full Ubuntu reinstall, as the issue with fstab has nothing to do with grub.

---

### Post by Zilioum on 2010-05-23
Ok, might really be easier. Do you have any idea what might have happened? So at least I can learn something new :D

Cheers

---

