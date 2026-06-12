---
title: "backup restore in 11.10"
date: 2012-01-20
forum: General Help
---

### Post by swayam on 2012-01-20
Hi All,

I have installed ubuntu 11.10 through wubi on my XP . It was good till 1/13 and then i messed up with the boot menu and i no longer find ubuntu to start. I have already taken backup of my old files using the backup tool supplied with 11.10. Now i have to re-install the ubuntu and i need to repack all the files from my backup folder. But the backup tool is no longer recognizing my backup zips.   I have tried to change the manifest file's hash map content to take the old backups but no way i can restore them. There is already 30 gb backup ... Please help :-(

---

### Post by bcbc on 2012-01-21
Do you still have the original root.disk (in Windows it's in \ubuntu\disks\root.disk )? If so, you can get your data from that.

I don't know much about dejabackup (is that what you used)?

---

### Post by swayam on 2012-01-21
yes i have used the dejabackup for the backup task. i have reinstalled the ubuntu from the iso again and lost all the previous root.disk. All i have is the backup taken in my window disks by the tool. I had taken full system backup without any encryption. So i have about 300 gz files . But i am not sure if it will be a successful effort to unzip the folders and copy all the files back to the corresponding file system. Because there are more than 2,3 zip which contains /home,/etc/,/bin etc so which one to copy back ?

---

### Post by bcbc on 2012-01-21
> **swayam said:**
> yes i have used the dejabackup for the backup task. i have reinstalled the ubuntu from the iso again and lost all the previous root.disk. All i have is the backup taken in my window disks by the tool. I had taken full system backup without any encryption. So i have about 300 gz files . But i am not sure if it will be a successful effort to unzip the folders and copy all the files back to the corresponding file system. Because there are more than 2,3 zip which contains /home,/etc/,/bin etc so which one to copy back ?
As I said - I don't know a lot about deja backup. Never used it myself. Hopefully someone else will step in to help.

---

