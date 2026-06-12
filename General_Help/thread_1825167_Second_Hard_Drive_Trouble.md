---
title: "Second Hard Drive Trouble"
date: 2011-08-14
forum: General Help
---

### Post by brianmulhall on 2011-08-14
i have cobbled together a machine for me to use ubuntu on and my idea was to have two hdd's but the second drive is present on the desktop with an icon and I  formatted using Gparted and i gave it an ext3 file system because I wasn't sure what would be more appropriate. But anyway this drive has only one folder inside labeled lost and found which is limited to only admin access and i went to the BIOS and the drive configuration section and the drive was listed as off so I set it from off  to auto which was my only other choice to see if that would help but I don't think it did anything.

 I can open the file System icon and then I just dont think this drive is really integrated into my system yet can anyone give an Idea of why the BIOS said it was off or undetected when I could actually access it on the desktop and do u think that the ext3 filesystem is good? Also if the BIOS is as is after i checked auto can i test it somehow to make sure i can save files there because i tried once without success before playing with the BIOS.

The computer is Dell Dimension 4600

---

### Post by pqwoerituytrueiwoq on 2011-08-14
you have to set the permissions on it
chown $USER:$USER or chmod 1777 the folker it mounts to
eg sudo chmod 1777 /media/storage
you can put a ntfs system on it since it lacks permission settings

---

