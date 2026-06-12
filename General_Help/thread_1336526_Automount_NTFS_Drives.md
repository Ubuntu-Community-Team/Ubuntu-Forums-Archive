---
title: "Automount NTFS Drives"
date: 2009-11-24
forum: General Help
---

### Post by Grets Sirob on 2009-11-24
I'm running Xubuntu 9.10, dual-booting with Windows XP, on a Compaq Presario R4000 laptop. I've got an extra NTFS partition between Windows and Linux that I'm using for data (music, documents, downloads, etc.). When I load up Xubuntu and log in, I have to manually mount the two other partitions to be able to us them. The system is detecting them, because if I, say, open the desktop settings dialogue and search for an alternate image, it can see the other two filesystems... I then have to input my password, and it'll mount the system so that I can use a background on that partition.
I don't want to have to do that. I want to be able to load up Xubuntu with it already mounted.  This is partly because I have several programs linked to information on the data partition, and they won't work unless I manually mount the disk.
I tried editing fstab to add the following lines:
```
/dev/sda1    /media/Windows
/dev/sda5    /media/Transdrive
```
But that didn't work. Do I need to put more info into fstab? Should I be doing something else? I've seen some stuff on using Hal, but after peering into that, I determined that I was definitely not geek enough to make that happen without someone holding my hand... ;)
I appreciate any advice you guys can give me!

---

### Post by VCoolio on 2009-11-24
Try like this:
```
/dev/sda1    /media/Windows      auto    user,defaults 0 0
/dev/sda5    /media/Transdrive      auto    user,defaults 0 0
```

---

### Post by Zoot7 on 2009-11-24
You need to specify the filesystem and the necessary parameters to successfully read and write.

Try adding this to fstab:
```
/dev/sda1    /media/Windows      ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda5    /media/Transdrive      ntfs-3g defaults,locale=en_US.utf8 0 0

```

Then to test it do:
```
sudo mount -a
```

---

