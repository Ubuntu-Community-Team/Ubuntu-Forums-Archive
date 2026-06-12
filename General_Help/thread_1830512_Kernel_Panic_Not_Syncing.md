---
title: "Kernel Panic Not Syncing"
date: 2011-08-21
forum: General Help
---

### Post by RFXCasey on 2011-08-21
Hey all, I recently moved a hard drive from one machine to another and visa-verse. Both were boot drives and one of the computers took the swap no problem, it fired right up and all is working fine. The other machine however isn't liking the swap and is kicking back with a 'Kernel Panic Not Syncing: VFS: VFS: unable to mount root FS on unknown-block 0,0'. I can boot the machine with a live disk but don't know how to get onto the hard drive to look at the lilo config or the Grub2 config. If I do get onto the hard disk however I really don't know exactly what I should change to get the computer working properly. Could someone please help me cause if I have to format the drive and reload all the software it is really going to be a huge pain, not that is isn't already but I would rather avoid this if at all possible. Thanks.

---

### Post by blazemore on 2011-08-22
> **RFXCasey said:**
> Hey all, I recently moved a hard drive from one machine to another and visa-verse. Both were boot drives and one of the computers took the swap no problem, it fired right up and all is working fine. The other machine however isn't liking the swap and is kicking back with a 'Kernel Panic Not Syncing: VFS: VFS: unable to mount root FS on unknown-block 0,0'. I can boot the machine with a live disk but don't know how to get onto the hard drive to look at the lilo config or the Grub2 config. If I do get onto the hard disk however I really don't know exactly what I should change to get the computer working properly. Could someone please help me cause if I have to format the drive and reload all the software it is really going to be a huge pain, not that is isn't already but I would rather avoid this if at all possible. Thanks.

Try booting into a lie CD and running
```
sudo grub-install /dev/sda
```

---

