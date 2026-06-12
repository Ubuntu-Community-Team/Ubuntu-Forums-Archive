---
title: "nvidia installation question"
date: 2011-10-28
forum: General Help
---

### Post by nethero on 2011-10-28
I have an Nvidia 9400 GT card and I just got through installing the lastest drivers directly from the Nvidia website.  I was successful in installing the driver and everything appears to be working well.  However, I realize that if I upgraded my kernel that I would have to reinstall the nvidia drivers.  How would I go about reinstalling them?  Do I simply run the script again?  Will it overwrite the old module?  I don't want to run into one of those situations where I have two drivers running and they both cause conflicts with one another.

Oh, one more thing.  I noticed that after disabling the nouveau drivers and installing the NVIDIA drivers that my boot screen has a really low resolution.  How do I put this back to the resolution I had with the nouveau drivers?

---

### Post by dino99 on 2011-10-28
why dont you install nvidia-current from synaptic ? dkms deals with new driver package upgrade

---

### Post by nethero on 2011-10-30
> **dino99 said:**
> why dont you install nvidia-current from synaptic ? dkms deals with new driver package upgrade

I tried that since it seemed to be the easiest thing to do, however, my bootscreen still had the same low resolution to I tried the most recent drivers.  Also, I already have the latest version installed and I'd rather use since I already have it up and working.

Has anyone gotten the boot screens to show at a higher resolution after upgrading?

---

