---
title: "Windows drive not showing in Lucid"
date: 2010-07-01
forum: General Help
---

### Post by smtouhid on 2010-07-01
I have installed Winxp & ubuntu 10.04. All are running excellently but i cannot brows my windows drive from lucid. in jaunty or karmic i use to work in ubuntu but all files were stored in windows drive. But in lucid i cannot find windows drives.

---

### Post by clrg on 2010-07-01
Please show me the output of 

```
sudo fdisk -l
```

and

```
mount
```

---

### Post by Leppie on 2010-07-01
put yourself in the fuse group and install ntfs-config:
```
sudo apt-get install ntfs-config
```
set the desired mount point and you're ready to go.

---

### Post by celldweller1591 on 2010-07-01
install ntfs-3g from software center and done :)

---

