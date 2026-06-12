---
title: "file pernissions on ntfs external drive"
date: 2009-10-05
forum: General Help
---

### Post by blur xc on 2009-10-05
I noticed that on my external ntfs drive, ALL files belong to root:root and have 777 permissions.  How does linux manage file permission on files and file-systems where neither of which where created in linux?  

Thanks,
BM

---

### Post by kanikilu on 2009-10-05
NTFS doesn't support unix permissions, so you can't change the permissions of files on that drive.

Check out the following page: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by t0p on 2009-10-05
> **kanikilu said:**
> NTFS doesn't support unix permissions, so you can't change the permissions of files on that drive.

Check out the following page: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Can you advise what we're supposed to learn from the linked page?  All I can see that's relevant is the line saying there are limitations re changing NTFS file ownership and access rights.  Which you already told us.

---

### Post by kanikilu on 2009-10-05
> **t0p said:**
> Can you advise what we're supposed to learn from the linked page? Just backing up what I said. Also, there are links on that page that might give him more information depending on what the OP wants to achieve. He doesn't explicitly say what he wants to do, but if he wants to change the permissions on those filesystems, for example, that can be done with a mount option:

> ntfs/vfat = permissions are set at the time of mounting the partition with umask, dmask, and fmask and can not be changed with commands such as chown or chmod. The [source](https://help.ubuntu.com/community/Fstab#Options) of that quote is in the external links of the page I gave originally...

---

### Post by blur xc on 2009-10-05
Thanks for the information.  I'm just curious for the sake of understanding how it works.  I'm not trying to change anything...

BM

---

