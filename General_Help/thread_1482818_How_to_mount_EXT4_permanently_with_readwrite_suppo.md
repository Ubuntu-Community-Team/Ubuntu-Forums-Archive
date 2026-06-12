---
title: "How to mount EXT4 permanently with read/write support."
date: 2010-05-14
forum: General Help
---

### Post by sikander3786 on 2010-05-14
Hi.

I have created 700 GB ext4 logical partition on my HDD. It is named sda7. Now I don't have read/write permissions, only root has those permissions.

How to change read/write permissions and how to mount it permanently?

Regards.

---

### Post by Nythain on 2010-05-14
First thing i would do is open a terminal, and type
blkid

find the drive and copy the UUID
then open up /etc/fstab with sudo permission and add a line similar to

UUID=<uuid>     /place/to/mount     ext4     defaults    0     2

that will get it to mount at the mount point (if that place exists) during boot
then a simple

sudo chown <username>:<username> /place/to/mount

should give you the permissions you need to read and write to it
at least thats what i always do, probably better ways to get it done, but its what i know

---

### Post by sikander3786 on 2010-05-14
Thanks Nythain.

It worked like a charm.

Sikander.

---

### Post by Drdog on 2010-09-26
also in my /media/ file there is a folder in there named after the UUID I'm trying to mount and when I click on it I get 

"You do not have the permissions necessary to view the contents of "712848ed-766a-4762-bf81-cda65954b115".

---

