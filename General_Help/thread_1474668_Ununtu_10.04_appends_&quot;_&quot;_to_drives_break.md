---
title: "Ununtu 10.04 appends &quot;_&quot; to drives breaking my shortcuts"
date: 2010-05-06
forum: General Help
---

### Post by exo14 on 2010-05-06
Just finished installing 10.04 and my partition labeled "DataDrive" has been changed to "DataDrive_".  Any ideas, or solutions would be greatly appreciated.

---

### Post by viralmeme on 2010-05-06
> **exo14 said:**
> Just finished installing 10.04 and my partition labeled "DataDrive" has been changed to "DataDrive_".  Any ideas, or solutions would be greatly appreciated.
Ubuntu mounts the drives using the label. If the mount point already contains a directory of the same name then it uses _. Remove the empty DataDrive directory and Ubuntu will link it back to the correctry mount at reboot.

---

### Post by michy99 on 2010-05-06
Is this partition on an internal or external drive? Do you have an entry for this partition in /etc/fstab? Is the partition labeled?

It sounds like the partition is labeled 'DataDrive' and Ubuntu is trying to mount it in /media using that label, but there is already a directory named DataDrive, so it mounts as DataDrive_ instead to differentiate. If that is what is happening, you should unmount the partition, delete the /media/Datadrive directory, and when you remount the partition it should be at /media/DataDrive.

Edit: I guess I type too slow. Anyway, what he said.

---

### Post by exo14 on 2010-05-06
Thanks ymitchell and michy99 that was the problem.  I appreciate the help.

---

### Post by dcstar on 2010-05-07
> **ymitchell said:**
> Ubuntu mounts the drives using the label. If the mount point already contains a directory of the same name then it uses _. Remove the empty DataDrive directory and Ubuntu will link it back to the correctry mount at reboot.

Just another reason why users should **never, ever put things in system folders** like /media.

---

