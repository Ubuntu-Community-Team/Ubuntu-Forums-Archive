---
title: "Files from previous ubuntu installation?"
date: 2009-11-05
forum: General Help
---

### Post by piggelbos on 2009-11-05
Hi all,

I've been using Ubuntu for a couple of years now and really like it! Yesterday I tried to upgrade my kernel from 9.04 to 9.10. After that my pc wouldn't boot anymore. It said something like: "Kernel Panic - Not syncing".

Because there are files in there that I needed I bought another HD and installed 9.10 on it. So now that the computer is functioning normal again I would like to get the files from the other HD. If I just mount the HD in Ubuntu I only see the filesystem (not my files). 

The HD doesn't boot anymore because it is an external HD and I installed my new ubuntu on an internal HD (wich also holds the bootfile).

Is there an possibility that I can add that HD to the current bootloader again so I can try to fix the kernel problem? Or is there an other way to get my files back without booting it?

Thanks in advance!

Grtz Jeroen

---

### Post by P4man on 2009-11-05
Unless you encrypted your homefolder there should be no reason to revive the old install to retrieve your files.

Normally you should be able to mount the drive by just going to places > nameofyourdrive

Then browse further to:

/media/nameofdrive/home/youroldusername

If that doesnt work can you post the output of

```
sudo fdisk -l?
```

---

