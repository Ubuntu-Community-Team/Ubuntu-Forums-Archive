---
title: "upgraded to 12.04 and now have some problems"
date: 2012-05-30
forum: General Help
---

### Post by jlh68 on 2012-05-30
MY /home partition is now mounting under /media, instead of being part of my setup like it was before upgrading.  How do I change the mount point and what do I change it to so I have immediate access?

I upgraded from 10.10 to 12.04 and all my applications have to be reinstalled also.  Lost my emails, but I did archive the email addresses.  All my data was on the /home partition so it was unchanged, no loss of data wven though I copied my /home partition to an external HD.

I wish I knew how to save all the settings and such before upgrading versions.  I don;t have this problem when updating versions.

---

### Post by Zvlwab on 2012-05-31
You can edit mount points in the file /etc/fstab
More details depend on your drive.

Before rebooting after editing, you need to remove your current home dir, because you cannot mount a partition as a folder that is not empty.

---

