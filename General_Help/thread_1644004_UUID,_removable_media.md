---
title: "UUID, removable media"
date: 2010-12-12
forum: General Help
---

### Post by Dave_L on 2010-12-12
If I use an external USB hard drive that's not always connected, will the drive always have the same UUID?

If I connected a different external drive, would it have a different UUID, but one that's always the same for that drive?

If so, how does that work?  Is the UUID stored on the drive, or based on the drive's hardware characteristics?

---

### Post by The Cog on 2010-12-12
The UUID is written to a partition as it is formatted. The UUID will remain the same until the partition is reformatted. I don't know of a way to change the UUID without reformatting, or to reformat but retain the UUID.

If a drive has several partitions, each partition has its own UUID, so it's not related to the drive itself, but independently to each partition on the drive.

EDIT:
Coincidentally, I just saw in another post how to change the UUID of an ext3/4 partition without reformatting it (if you're interested):
sudo tune2fs /dev/whatever -U UUID

---

### Post by dcstar on 2010-12-13
> **Dave_L said:**
> If I use an external USB hard drive that's not always connected, will the drive always have the same UUID?
.......

If you actually want External Drive partitions to mount to the same place every time, simply LABEL all of them (uniquely) and they will be mounted with the Label name.

---

### Post by Dave_L on 2010-12-13
I'm setting up a backup script that will check whether a particular external drive (partition) is mounted, and use that as the destination.

It sounds like either a UUID or a label will work here.

Thanks for the help. :)

---

### Post by The Cog on 2010-12-13
For that, I would suggest that a label makes more sense. That's what I do. I had a really original and ingenious idea, and called my drive BACKUP.

---

