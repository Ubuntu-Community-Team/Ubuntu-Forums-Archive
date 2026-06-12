---
title: "Mounted data stored where?"
date: 2011-07-05
forum: General Help
---

### Post by paulrosk on 2011-07-05
Does anyone know WHERE Ubuntu stores the location for mounted external filesystems and/or servers? I can mount other computers on my network, display the files etc., but CAN NOT find where Ubuntu saves the mounted system data and locations. 

i.e.

I mount a PC on the network, open a file manager window and see everything, but can't find where Ubuntu has that system "mounted". It's NOT in the /mnt folder or anywhere else I can see. I need to find this location to feed it to a program that sets up a remote server. I can't setup the server because the program only "looks" at the local root and doesn't find any external mounts.

---

### Post by wildmanne39 on 2011-07-05
> **paulrosk said:**
> Does anyone know WHERE Ubuntu stores the location for mounted external filesystems and/or servers? I can mount other computers on my network, display the files etc., but CAN NOT find where Ubuntu saves the mounted system data and locations. 

i.e.

I mount a PC on the network, open a file manager window and see everything, but can't find where Ubuntu has that system "mounted". It's NOT in the /mnt folder or anywhere else I can see. I need to find this location to feed it to a program that sets up a remote server. I can't setup the server because the program only "looks" at the local root and doesn't find any external mounts.
Hi, that is where it should be since it is not, open disk utility and see if it is there and you can mount it from within disk utility, then it will show up in file manager.

---

### Post by mcduck on 2011-07-06
That depends on how you mount the remote locations. If you use fstab, then the locations are defined there. If it's about automounted removable drives, take a look in /media. And if you are mounting remote locations using the file manager's "Connect to server"-option, you should find the locations in ~/.gvfs

---

