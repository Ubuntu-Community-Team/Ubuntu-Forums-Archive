---
title: "Read Only File System !!"
date: 2010-04-05
forum: General Help
---

### Post by Diptansu on 2010-04-05
I am having a strange problem. I have a near 200 GB partition. Fat 32.

I was copying some files into that and suddenly my computer shut down due to overheating .. am having this problem for some days ..

Anyway .. After I restarted it I found I am not being able to any thing except copying for the drive .. Otherwise I dont have permission.

I cannot even change the permission into 'Create and Delete' while its saying "Read only filesystem" ..

When I restart the comp, everything seems okay .. but after a few seconds the problem arise .. it become inaccessible .. I simply cannot even creat a folder .. 

Help me please .. :(

---

### Post by ugm6hr on 2010-04-05
Bizarre... vfat does not have permissions, I thought.  Which is why you can't change them.

---

### Post by 3rdalbum on 2010-04-05
I've had this happen as well, although not on a vfat partition.

It's caused by bad filesystem damage. Linux sees that the filesystem is damaged and remounts the partition as read-only to prevent further damage.

Unmount the partition and use the "fsck" command on it; but usually when it gets this bad you will eventually need to reformat the partition.

---

### Post by Diptansu on 2010-04-05
:D .. even before reading this i have already reformatted the partition .. and everything is well now .. :)

Thank you guys ..

---

