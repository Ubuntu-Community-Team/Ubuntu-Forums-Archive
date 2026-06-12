---
title: "Data Partition using Separate Trash"
date: 2012-02-27
forum: General Help
---

### Post by mprocter89 on 2012-02-27
Hi everyone. I currently have all my Documents, Videos, Pictures, and Music on a separate Data Partition that I mount with a bind mount in the fstab. It's working great, however, whenever I delete any files in those folders, instead of going into the trash can they all go into a separate '.trash' folder that is created.

e.g. If I delete ~/Pictures/0001.jpg it goes to ~/Pictures/.trash/items/0001.jpg

I then have to go into this folder and delete the file again for it to be sent to the trash can. Is there any way to send a file directly to the trash, bypassing this step?

I'm running Natty if that makes a difference.

---

