---
title: "Lost HFS+ Functionality?"
date: 2012-01-27
forum: General Help
---

### Post by C4B4L on 2012-01-27
I updated my Ubuntu 11.10 computer earlier today and found out that I had lost the ability to write to my HFS+ partition, something I could do immediately before the update. I had created the partition with hfsprogs and was using it so I could eliminate case sensitivity errors from Wine. I don't have access to a Mac, so messing with journaling is not an option and I don't have the hard drive space to backup the data and reformat so that's not an option either unless I want to use a 2GB thumb drive to shuttle 60GB worth of data to another computer.

Does anybody have any ideas on how to fix this or am I just screwed?

---

### Post by C4B4L on 2012-01-27
I fixed it. I just needed to use fsck.hfsprogs. Apparently it was unmounted improperly when I restarted the computer after the update.

---

