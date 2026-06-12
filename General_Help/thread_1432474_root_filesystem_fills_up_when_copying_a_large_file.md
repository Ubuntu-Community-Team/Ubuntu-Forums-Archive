---
title: "root filesystem fills up when copying a large file"
date: 2010-03-17
forum: General Help
---

### Post by etech22 on 2010-03-17
Hi,

I was just copying a large (50GB) file from one mounted partition to another mounted partition (a USB drive), but before the operation completed, my root filesystem, on a separate partition, filled up. Because it filled up I also couldn't get past the login when I rebooted. I think this is because there is no room to load temporary files. I'm expanding the root partition to temporarily fix this.

My question is, how can I avoid my root file system filling up when copying a massive file between mounted partitions? I'm assuming the reason this is happening is that the file is being cached in root during the transfer. 

Any ideas?


etech

---

### Post by audiomick on 2010-03-17
I think your theory is probably correct, but can't suggest a solution, I am afraid.
How big is your / partition? Most people here recommend, as far as I have seen, between 10 and 15 GB, assuming that /home is a separate partition. If it is significantly smaller than that, I would consider making it bigger and leaving it so.

---

### Post by etech22 on 2010-03-17
Hi,

Thanks for the reply.

After getting back into the system, it appears that the file was actually copying into a /media/USB50GB folder, rather then to the mounted USB drive, also named USB50GB. 

Is this a problem with the USB drive name? I recently renamed it after formatting it to ext4. Changed the name using e2label from "2345234randomncharacters" to "USB50GB".
How can I fix this?


etech

---

### Post by audiomick on 2010-03-18
> **etech22 said:**
> ... copying into a /media/USB50GB folder, rather then to the mounted USB drive, also named USB50GB. 

I think you will find that the folder is the drive. /media is there as a mount point for removable media, and it would be normal, as far as I know, for a USB drive to turn up there as /media/nameofdrive.

---

