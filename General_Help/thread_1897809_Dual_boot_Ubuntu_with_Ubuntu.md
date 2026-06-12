---
title: "Dual boot Ubuntu with Ubuntu"
date: 2011-12-19
forum: General Help
---

### Post by m3bik on 2011-12-19
I'm working on customizing an Ubuntu OS. I've been working on the "development" side for a while. I wanted to install a "working" copy on the same computer for test purposes. I used remastersys to create an iso and then attempted to install the ISO side by side with the current Ubuntu install.. When installing, I selected install side-by-side, resized the partition space, and then installed.

My grub menu only has the new install listed. The original "development" one is not listed. However, when I log into the only option available, I do see that the other Ubuntu install is still on the hard drive and available for me to browse..

How can I get them both listed on grub? When running the os-probe command, it only finds one os.. not both! Please help!

---

### Post by oldfred on 2011-12-19
When remastersys restored, did it restore using the same UUID?
To see UUIDs:
```
sudo blkid
```

If they are the same you have to edit one to have different UUID and then change fstab & grub to use the correct new UUID.

Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

---

