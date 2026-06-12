---
title: "Changing order of start up programs - dropbox problem"
date: 2011-06-14
forum: General Help
---

### Post by socistep on 2011-06-14
Hi All

Have tried to find a solution but no luck so far.

I run Ubuntu 10 and on start up I set Dropbox to automatically open, however I've not been able to get this to run correctly.

The reason is that it can't find my dropbox folder location, this is /home/ian/documents/dropbox however ../documents is located on my media server and is mounted on boot via fstab so the obvious issue is that dropbox is opening before the NFS share has been mounted hence the folder is missing.

Does anyone know how I might approach fixing this? Am happy to get into start up scripts in init.d etc. to re-order/solve this problem but need some advice on where to look.

All help appreciated!

Thanks in advance
Ian.

---

