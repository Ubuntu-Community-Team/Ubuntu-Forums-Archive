---
title: "Removing file systems (partitions) from &quot;Places&quot;"
date: 2010-01-28
forum: General Help
---

### Post by Mahngiel on 2010-01-28
I don't need the Windows nor System Reserved (Win7 Backup fs) to be visible. If i wanted to, i could mount them via terminal.  So how do i remove them from the list as my two other nix partitions are?

---

### Post by Mahngiel on 2010-01-29
*bumpity*

---

### Post by chewearn on 2010-01-29
The workaround appears to be to add fstab entries to mount them in /mnt
I haven't tried it, so can't confirm if it will work though.

[https://answers.launchpad.net/ubuntu/+question/16593](https://answers.launchpad.net/ubuntu/+question/16593)

---

### Post by akshay.sulakhe on 2010-01-29
that will work,while installing,give the mount points as /mnt...or after installation create the name of the dir's,in the specific locations and then edit ur fstab....

---

### Post by Mahngiel on 2010-01-31
confirmed. thank you.

---

