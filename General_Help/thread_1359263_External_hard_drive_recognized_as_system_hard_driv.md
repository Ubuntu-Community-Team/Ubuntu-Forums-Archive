---
title: "External hard drive recognized as system hard drive"
date: 2009-12-19
forum: General Help
---

### Post by winecurmudgeon on 2009-12-19
I installed 9.04 as a dual boot with Vista, which worked well. But I made the mistake of leaving my external drive attached when I installed Ubuntu, and now I can't disconnect the external drive without Ubuntu crashing. The system apparently recognizes the external drive as a system hard drive, and mounts it whenever I boot up. If it isn't there to be mounted, I can't get into Ubuntu.

I'd like to find a way to fix this, so that the external drive acts like an external drive. It's not a huge problem, since I can unmount the external drive after Ubuntu loads and it usually behaves. But sometimes, it does annoying things -- like spinning, which slows down the entire system, and I have also had problems trying to save files. The system hangs up, as if it's stuck looking for where to put the file.

Can I use Gparted to disconnect the external drive? How would I do it? Or do I need to use a Live CD and its version of Gparted?

Thanks for any thoughts.

---

### Post by dcstar on 2009-12-19
> **winecurmudgeon said:**
> I installed 9.04 as a dual boot with Vista, which worked well. But I made the mistake of leaving my external drive attached when I installed Ubuntu, and now I can't disconnect the external drive without Ubuntu crashing. The system apparently recognizes the external drive as a system hard drive, and mounts it whenever I boot up. If it isn't there to be mounted, I can't get into Ubuntu.

I'd like to find a way to fix this, so that the external drive acts like an external drive. It's not a huge problem, since I can unmount the external drive after Ubuntu loads and it usually behaves. But sometimes, it does annoying things -- like spinning, which slows down the entire system, and I have also had problems trying to save files. The system hangs up, as if it's stuck looking for where to put the file.

Can I use Gparted to disconnect the external drive? How would I do it? Or do I need to use a Live CD and its version of Gparted?

Thanks for any thoughts.

Remove the entry for it from the /etc/fstab file, and if you accidentally installed Grub onto it during installation you will have to reinstall Grub onto an internal drive (search for detailed instructions).

---

### Post by winecurmudgeon on 2009-12-20
Thanks for the answer. How can I tell if I installed GRUB on the external drive? Will it show up when the system asks me which drive I want to boot to?

---

### Post by dcstar on 2009-12-20
> **winecurmudgeon said:**
> Thanks for the answer. How can I tell if I installed GRUB on the external drive? Will it show up when the system asks me which drive I want to boot to?

This will show you the disks the system can see, you will have to figure out what is what:
```
sudo fdisk -l
```

---

### Post by winecurmudgeon on 2009-12-21
Thanks again. Sounds like something I can try to figure out over the holiday weekend -- rebuilding the GRUB!

---

