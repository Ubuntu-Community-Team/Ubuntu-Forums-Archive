---
title: "Might have added a hard drive improperly to a RAID 5 -- is this ok?"
date: 2011-08-07
forum: General Help
---

### Post by tweek3867 on 2011-08-07
Hi! I hope I put this in the right forum. I'm new to posting here, so sorry if I did!

I just installed a new hard drive in my computer and added to an existing raid managed via mdadm. Currently, the other three drives are listed under:

/dev/sda1
/dev/sdb1
/dev/sdc1

But when I added the new drive, I mistakenly added it as /dev/sdd, rather than /dev/sdd1. It seems to be growing fine, but I was curious if this is a problem. Will it cause any issues / should I remove and re-add it as /dev/sdd1, or will it be fine?

Thanks for any help or insight you can provide!

---

