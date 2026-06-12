---
title: "change properties error message"
date: 2011-06-15
forum: General Help
---

### Post by gandaran on 2011-06-15
every time I paste any file in the windows D ntfs partition there's an annoying message it wasn't able to change the file properties, why does this happens from using kubuntu only but not from ubuntu?

---

### Post by gandaran on 2011-06-17
bump

---

### Post by ruffEdgz on 2011-06-17
> **gandaran said:**
> every time I paste any file in the windows D ntfs partition there's an annoying message it wasn't able to change the file properties, why does this happens from using kubuntu only but not from ubuntu?

Is the NTFS drive mounted manually or through fstab?
What options are used when mounting the NTFS drive?

It seems like either Ubuntu gives the proper permissions to that NTFS drive and not on Kubuntu but it isn't known until we know more on how they are mounted on both distros.

---

### Post by gandaran on 2011-06-21
> **ruffEdgz said:**
> Is the NTFS drive mounted manually or through fstab?
What options are used when mounting the NTFS drive?

It seems like either Ubuntu gives the proper permissions to that NTFS drive and not on Kubuntu but it isn't known until we know more on how they are mounted on both distros.

fstab mount
```
# /windows/D was on /dev/sda3 during installation
UUID=0BE284C01165D33C /windows/D ntfs    defaults,umask=007,gid=46 0       0
```
code is the same like on ubuntu, could be some KDE bug but I would like to get rid of that annoying message window.

---

