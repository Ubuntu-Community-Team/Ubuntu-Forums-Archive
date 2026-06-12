---
title: "Extending the size of ntfs partion through gpared (screen added)"
date: 2009-10-22
forum: General Help
---

### Post by emigrant on 2009-10-22
hi,
i want to delete sd7 (which is ubuntu 7.04 which i no longer use) and add it to sd1 (vista). how can i do it?
I didnt play around fearing i might lose some thing which might endup in broken system.
already i had a bad experience in loosing the grup file.

thank you for your help.

[IMG]http://img203.imageshack.us/img203/3672/screenshotdevsdagpartedm.png[/IMG]

---

### Post by louieb on 2009-10-22
Other that deleting it and moving all the partitions between the now  unallocated space and sda1 to the right. Don't see any other way - and that does not look like a very safe way to go.  Just don't see it being worth the risk of moving all those partitions for 2GB disk space.

Just a thought. You could free up some space in sda1 by formatting sda7 with NTFS and putting the Windows virtual memory file in sda7.

---

### Post by P4man on 2009-10-22
boot from livecd
run partition editor
right click the swap partition and select "swapoff"
delete the partition you no longer need.
move sda5 to the right
resize sda4 (the extended partition which is like a container for the  others inside)
Move or delete sda3, Dont see why youd need it. One swap partition is enough

move sda2 to the edit: right
resize sda1

click apply

Go buy something for your girlfriend, watch a movie, go out, have a drink (it will take some time)

---

