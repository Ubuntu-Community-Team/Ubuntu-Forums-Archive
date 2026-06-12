---
title: "virtual cd drive"
date: 2010-06-08
forum: General Help
---

### Post by creatxr on 2010-06-08
i want to emulate a directory as a cdrom drive. thanks.

---

### Post by pytheas22 on 2010-06-08
You can mount ISO images as if they're CDs by right-clicking and selecting "Open with Archive Manager," but that won't work for directories.  If you give more information about what exactly you're trying to do (why you want to make a directory act like a CD drive), maybe we can come up with a solution.

---

### Post by creatxr on 2010-06-08
i want to use some files in vmware player, i don't want to copy it to vm, and i don't want to make a .iso, so it's better if there is a way to emulator a directory as a cdrom

---

### Post by _khAttAm_ on 2010-06-09
As far as I know, it is not possible to mount folder as a CDROM.. You should probably try sharing via network.

---

### Post by pytheas22 on 2010-06-09
So you want to mount a directory as if it were a CD in order to allow your virtual machine to access the files in the directory?  If that's the case, why not just share the directory over the network using NFS or samba so that both your host and guest can access the files?  I'm not sure about VMware, but I know that VirtualBox allows you to do this sort of thing very easily using the "Shared Folders" feature.

---

### Post by waynefoutz on 2010-06-09
I use gmount-iso. You can find it in synaptic.

---

### Post by _khAttAm_ on 2010-06-10
> **waynefoutz said:**
> I use gmount-iso. You can find it in synaptic.

it is just a front end to mount tool and it doesn't have an option to mount a directory as a CD-ROM

---

