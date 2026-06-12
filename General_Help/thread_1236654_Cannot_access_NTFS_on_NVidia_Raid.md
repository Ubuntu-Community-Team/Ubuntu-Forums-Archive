---
title: "Cannot access NTFS on NVidia Raid"
date: 2009-08-10
forum: General Help
---

### Post by Cubeology on 2009-08-10
The original configuration of this computer was Vista x64 installed on one of 2 partitions of a NVidia Raid 5 array.  The other partition holds about 1.2 TB of misc files.  I added another HDD (separate from the array) and installed Ubuntu 9.04.  I would like to be able to access the 2 NTFS partitions on the NVidia raid.  I have searched various forums online and installed DMRAID to access the raid, and NTFS-3G to access the NTFS.  Unfortunately, I have not been able to get anywhere trying to use these tools.  The only sign I see that the Raid array exists to ubuntu is the existence of /dev/mapper/nvidia_cecbhbhe.  I cannot figure out how to access the partitions.  Ultimately once I get ubuntu properly configured and adjust myself to the ubuntu, I would like to somehow convert the raid array to something native to linux, presumably ext3, but my immediate task is just figuring out how to read/write from the existing NTFS partitions.

---

### Post by ronparent on 2009-08-14
Sorry I missed your post. When dmraid is run it creates /dev/mapper. This directory contains the symbolic links to your raid partitions. The one(s) with numbers following are the mountable partitions. You can manually mount them with a mount command of the form **mount <sysmbolic_link_1> /media/<name_of_your_choice>**. Wherever you choose to mount them must be an eppty location manually created for the purpose. Simularly the raid partitions can be automatically mounted on boot by adding like notations in /etc/fstab. Give a yell if this isn't specific enough.

---

### Post by TotoTheDog on 2009-08-14
> **ronparent said:**
> Sorry I missed your post. When dmraid is run it creates /dev/mapper. This directory contains the symbolic links to your raid partitions. The one(s) with numbers following are the mountable partitions. You can manually mount them with a mount command of the form **mount <sysmbolic_link_1> /media/<name_of_your_choice>**. Wherever you choose to mount them must be an eppty location manually created for the purpose. Simularly the raid partitions can be automatically mounted on boot by adding like notations in /etc/fstab. Give a yell if this isn't specific enough.
 
Thanks, this helped me out as well.

---

