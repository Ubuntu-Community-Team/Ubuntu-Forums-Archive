---
title: "How i can install virtual clonedriver in ubuntu"
date: 2012-02-19
forum: General Help
---

### Post by uut on 2012-02-19
Hi,all!
I need virtual clonedriver in my ubuntu (gnome desktop)
How i can install it?
thanks a lot!

---

### Post by Paddy Landau on 2012-02-19
If you want to mount an ISO as a virtual CD or DVD, Ubuntu already has the functionality built in. There's no need to install anything.

As far as I know, there is no GUI to do this, but you can do it from the terminal. Open Terminal and enter the following command:
```
sudo mount -o loop *isofile* *mountpoint*
```For example, if your ISO is in your Downloads folder and you wish to mount in ~/mnt, enter:
```
sudo mount -o loop ~/Downloads/precise-desktop-amd64.iso ~/mnt
```To unmount, enter:
```
sudo umount ~/mnt
```

---

