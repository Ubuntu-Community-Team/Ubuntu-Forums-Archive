---
title: "adobe cs5 in wine? any ideas?"
date: 2010-12-12
forum: General Help
---

### Post by capitalfear on 2010-12-12
okay, i am using ubuntu 10.10
i am trying to basically put daemon tools on my laptop in the ubuntu partition, because i do not have any space left on my windows partition. so after that i want to open cs5 iso, on my daemon tools....any ideas? oh also, the isos are +5 gigs, any idea on how to burn them on discs? without splitting them into tiny chunks? maybe split in half? or not split at all and just burn? any help greatly appreciated with either subject

---

### Post by Verbeck on 2010-12-12
to mount an iso file
1. click the iso file>open with other application>archive mounter to 

2. or from a terminal:
```

sudo mkdir /media/ps
sudo mount /path/to/iso/image.iso /media/ps -t iso9660 -o loop

```3. else install gmountiso from the software center and use it to mount the iso file (applications>system tools)

edit: doesnt look like it would run nicely [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)

---

### Post by capitalfear on 2010-12-12
naw man i can mount it, i just wanted some of the..."abilities" that daemon provides. and thanks, i still need to burn large files on disks...

---

