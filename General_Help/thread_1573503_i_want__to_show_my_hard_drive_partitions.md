---
title: "i want  to show my hard drive partitions"
date: 2010-09-12
forum: General Help
---

### Post by miroooo on 2010-09-12
i already installed a netbook remix on my sony vaio 11.1 inch laptop
i do not know anything about mountpiont  thing 
i can not view my partitions 

any help totally appreciated........


thank you

---

### Post by mr_luksom on 2010-09-12
Try opening gparted. can you post what you can see?

If it is mounted, it will show the drive in the upper right drop box. The. you can see if your partitions are there.

Be careful not to change anything though....

---

### Post by 73ckn797 on 2010-09-12
Check out these links:
[https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by drs305 on 2010-09-12
For a GUI app, you can go to System Administration, Disk Utility. Once you click on a drive/partition, information will be displayed. On the left side is an option to mount or unmount the partition. On the right, you can see where it is currently mounted.

If you want the partitions displayed on the Desktop, run this command (or open the Configuration Editor - gconf-editor - and go to):
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'true'
```

---

### Post by Mark Phelps on 2010-09-13
> **miroooo said:**
> i already installed a netbook remix on my sony vaio 11.1 inch laptop
i do not know anything about mountpiont  thing 
i can not view my partitions 

any help totally appreciated........


thank you

You can get a quick listing by opening a terminal and entering "sudo fdisk -lu" (that's a lowercase L, not a one).

---

