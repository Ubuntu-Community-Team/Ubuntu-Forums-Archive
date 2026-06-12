---
title: "permissions on mounted ntfs drive"
date: 2009-08-10
forum: General Help
---

### Post by adempewolff on 2009-08-10
I multi boot and store all of my personal data as well as my firefox profile (windows firefox and linux firefox still have not killed eachother sharing the profile, its amazing!) on a NTFS partition.

Because I wanted all personal data on its own partition and I needed Windows to be able to access it I decided against an ext3 /home partition (I did not trust loading ext2/3 drivers into windows and letting it mess with /home).

Instead I made it NTFS and created symbolic links between all the folders in my home folder and the folders on the partition.  This has worked great except for the Desktop.  With NTFS I must set permissions at mounting and I am having trouble with this.  For the desktop I obviously need execute priviledges for launchers at the very least.

Whats the best way to do this?  I find myself very confused about how permissions work with mounting NTFS.  Here is the line in my fstab as is:

```
UUID=6725E71243EB9925 /media/data ntfs-3g auto,nouser,fmask=137,dmask=027,uid=1000 0 0
```

What is the difference between fmask and dmask? is there any way I can get execute permissions on files for the desktop without enabling it for the entire drive?

Thanks for any help, sorry that I can't seem to answer these questions myself from the documentation and howtos!

---

### Post by adempewolff on 2009-08-10
or I suppose if someone has a better idea for a partitioning strategy if this is just not going to work well.  I am starting to understand why people hate ntfs...

---

### Post by asmoore82 on 2009-08-10
My guess would be that fmask is for files and dmask is for folders(directories).

I don't think there is an ideal way to reconcile the situation.

NTFS = DOS++

:P

---

### Post by adempewolff on 2009-08-10
yea I fixed my problem by spending a couple quality hours reading through documentation and then putting replacing the fmask and dmask parameters with umask=000 which gives read write and execute permissions for all files and directories.  not ideal, but probably the best I can do for now.

the only thing I was hoping I might be able to do is make the entire partition so execute is just for directory but then have the desktop have execute for files. I think the only way I could do this is to mount it seperately which isn't really something I want to do.

maybe I'll just make it ext3 and get the ext2/3 drivers for windows...

---

