---
title: "Dual Booting - Mirroring Folders"
date: 2011-07-30
forum: General Help
---

### Post by TmacD on 2011-07-30
I'm just wondering if it's possible to mirror a folder from another location. For example, say I want my Win7 Documents folder to be integrated with my Ubuntu Documents Folder, allowing changes to the folder from either OS. Is this possible?

---

### Post by dino99 on 2011-07-30
its not secure and absolutly not linux spirit

linux can read/write ntfs files via ntfsprogs & ntfs-3g (look at synaptic)

---

### Post by TmacD on 2011-07-30
Please excuse my ignorance, but how is it not secure?

---

### Post by mokrates on 2011-07-30
Your ntfs-partitions should be regognized by udisk and be displayed in the mounter-applet, (supposing you have one on your desktop) and in nautilus, dolphin, lxfileman whatever you use.
Integrating directlty with your documents-folder is not directly supported, because it's kinda complicated you could use 'aufs' or something, but you probably don't want that.
About security: The ntfs-3g driver is mature and stable and i haven't seen it corrupt volumes ever. But still, i think, it's kinda in a 'testing' stage.
And additionally: an on access virus scanner, you may have installed on your win7 is, of course, bypassed, if you write to your windows-volume from linux. But nobody should ever save documents he or she doesn't trust.

---

### Post by Megaptera on 2011-07-30
TMacD,
Have a look at this option, it might be more straightforward: Quote "What you can do is redirect the other commonly used folders like Documents, Downloads, Music, etc. to another partition, one that can be read by Windows.  Then, you can add these folders to your Windows 7 Libraries and mark them as the default save location."

Full guide here: [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by ajgreeny on 2011-07-30
> **Megaptera said:**
> TMacD,
Have a look at this option, it might be more straightforward: Quote "What you can do is redirect the other commonly used folders like Documents, Downloads, Music, etc. to another partition, one that can be read by Windows.  Then, you can add these folders to your Windows 7 Libraries and mark them as the default save location."

Full guide here: [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)
I would definitely go with this shared partition system for all your data files, formatted as ntfs and therefore read by windows automatically, and available in ubuntu if you use ntfs-config to ensure the partition is mounted at boot time.

---

### Post by TmacD on 2011-07-30
> **ajgreeny said:**
> I would definitely go with this shared partition system for all your data files, formatted as ntfs and therefore read by windows automatically, and available in ubuntu if you use ntfs-config to ensure the partition is mounted at boot time.

This seems like a simple way to do this; however, I already have four partitions already - Win7, Ubuntu, Ubuntu Swap, and the Win7 System Reserve. If I use ntfs-3g, should I still be able to have read/write access to folders within the Win7 partition (without the "integration")? If so, I can just sync the two sets of folders manually.

---

### Post by ajgreeny on 2011-07-30
Are any of your ubuntu partitions logical, within an extended partition wrapper?  If so it may be possible to use gparted on a live CD/USB and edit current partition table to add another shared within that wrapper, extended partition.

Can you run a live CD and show a screenshot of gparted which may help us.

---

