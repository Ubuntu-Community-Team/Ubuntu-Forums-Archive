---
title: "Mount a multi-sector image file?"
date: 2009-08-09
forum: General Help
---

### Post by OmegaWarrior on 2009-08-09
Is there any way to mount a multi-sector mdf file in ubuntu 9.04?  (Gnome)

I've seen that Acetoneiso doesn't support this feature, but I can't figure out if that's a tech problem or if it is purposefully not implemented for legal reasons.

Thanks

---

### Post by TonyQ on 2009-08-11
I have the same problem in Jaunty. An iso game (maybe multisector) 5,6Gb. None of the known iso programs worked (even not CDemu, which is supposed to work!). Pls help

---

### Post by bulletxt on 2009-08-12
> **TonyQ said:**
> I have the same problem in Jaunty. An iso game (maybe multisector) 5,6Gb. None of the known iso programs worked (even not CDemu, which is supposed to work!). Pls help

If you are sure it's an ISO file, it probably is an ISO with UDF file system. You can mount it from a shell. I don't remember the command, it should be something like "sudo mount -o loop udf image.iso /mount_folder

---

