---
title: "Automounting NTFS partitions in Lucid"
date: 2010-05-29
forum: General Help
---

### Post by oakdeveloper on 2010-05-29
Hi,

I am having a dual boot setup with Lucid Lynx and Windows 7. I want to automatically mount the NTFS partitions whenever I login to Lucid. I am looking for a graphical tool to set this up. Kindly suggest one.

Thanks,
Babu

---

### Post by VCoolio on 2010-05-29
Try [this one](http://pysdm.sourceforge.net/). I've not used it myself (it's not like you have to be a genius to edit /etc/fstab) but it is voted quite well in archlinux' AUR.

---

### Post by oakdeveloper on 2010-05-29
> **VCoolio said:**
> Try [this one]("http://pysdm.sourceforge.net/"). I've not used it myself (it's not like you have to be a genius to edit /etc/fstab) but it is voted quite well in archlinux' AUR.

Thanks! I tried it and it works perfectly.

---

### Post by Mark Phelps on 2010-05-29
> **oakdeveloper said:**
> Hi,

I am having a dual boot setup with Lucid Lynx and Windows 7. I want to automatically mount the NTFS partitions whenever I login to Lucid. I am looking for a graphical tool to set this up. Kindly suggest one.

Thanks,
Babu

Unless you're mounting it read-only, that's a really BAD idea.  I used to that and, whenever I had any filesystem related problems, that rendered by MS OS partition unbootable.

Better to mount it read-only; that way, you won't run the risk of corrupting the filesystem.

---

