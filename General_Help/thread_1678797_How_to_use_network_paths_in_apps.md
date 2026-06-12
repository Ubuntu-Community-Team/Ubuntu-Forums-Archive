---
title: "How to use network paths in apps?"
date: 2011-01-31
forum: General Help
---

### Post by nnn= on 2011-01-31
In nautilus I have smb://... but when I need to access that location from dialogs in other apps it doesn't work. E. g., "save page to" dialog in firefox.

---

### Post by piquat on 2011-01-31
Have you tried \\server_name\share_name?  Or sometimes I have better luck using the IP like smb://192.168.1.112/share_name.

You could mount the share and address it as if it were local.    /mnt/share_name.    If I were saving to the same share a lot I'd probably do this.

---

### Post by nnn= on 2011-01-31
First two didn't work in save dialogs, and \\... didn't work even in nautlius. Note that in the save dialog I prepended the path in front of the filename, because the address isn't typable. This method works for local paths.

By the way, it seemed to mount the share once for the time I used host name, and again when I used the ip address, so that I had shortcuts on desktop.

Local mount would most likely work, but I think it'd be easier to just save locally and then move files.

---

### Post by Morbius1 on 2011-01-31
When you do a "smb://..." in Nautilus you actually mount the remote share at the following location:

> /home/your-user-name/.gvfs/share-name on server-nameThat's the location your app needs to go to find the share's contents.

You need to enable "show hidden files" in the "save page to" dialog in firefox to see it.

---

### Post by nnn= on 2011-01-31
That worked. I had to browse for the location because prepending the whole path to filename didn't work. I added a bookmark for the share, but it doesn't show in the dialog.

---

