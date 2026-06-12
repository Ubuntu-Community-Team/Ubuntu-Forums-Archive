---
title: "Help removing Unbuntu with ultimatebootcd.com"
date: 2010-11-12
forum: General Help
---

### Post by twst123 on 2010-11-12
Need help reclaiming disk space and partitions:  I installed Ubuntu on my laptop and would like it removed because I need  the space back.  I have Windows XP and Ubuntu currently.

How can I remove Ubuntu and get the old partition back for Windows to use with the latest version of Ultimate Boot CD (ultimatebootcd.com V5.0.3)?

Thanks!

---

### Post by sikander3786 on 2010-11-12
If you've got an Ubuntu live CD, you can use it for repartitioning as it contains gparted.

Just delete the Ubuntu partition and the Swap partition and recreate a new partition (FAT/NTFS whichever you prefer).

You might need to restore the MBR for Windows XP. Was Grub installed? Do you see the Grub menu when you start your computer?

---

### Post by twst123 on 2010-11-12
Unfortunately, my Unbuntu installation was corrupted during an upgrade from older version (system crashed during the upgrade).  So I am not able to boot into Unbuntu now.  I have an Ubuntu 10.10 CD.

---

### Post by sikander3786 on 2010-11-12
Yes I was talking about the Ubuntu 10.10 CD. It contains gparted so can be used to delete Ubuntu partitions.

Once booted that, go to Terminal under Applications > Accessories and type

```
gksu gparted
```

Gparted will show up an you'll be able to delete the partitions there.

Be careful, don't delete your Windows partition by mistake :-)

If you are unsure which ones to delete, from the Terminal, post the output of

```
sudo fdisk -l
```

So we can have an idea of your current setup.

---

### Post by twst123 on 2010-11-13
Update: somehow I was able to uninstall ubuntu using Windows Add/Remove programs.  Then I added some memory to my old laptop and installed version 10.10 beside Windows and it appears to be working fine.  It even resolved my old Compaq Presario R3000 wireless issue.  Thanks

---

### Post by sikander3786 on 2010-11-14
> **twst123 said:**
> Update: somehow I was able to uninstall ubuntu using Windows Add/Remove programs.  Then I added some memory to my old laptop and installed version 10.10 beside Windows and it appears to be working fine.  It even resolved my old Compaq Presario R3000 wireless issue.  Thanks
Ahhh. That was a Wubi install. Neither you mentioned that nor I asked you about that. From your statement I assumed that you were properly dual-booting. But I was wrong :-(

Glad its sorted out.

---

