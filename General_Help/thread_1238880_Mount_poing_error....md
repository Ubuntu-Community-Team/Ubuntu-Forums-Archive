---
title: "Mount poing error..."
date: 2009-08-12
forum: General Help
---

### Post by sadi09 on 2009-08-12
Guys please help... I have accidently messed up one of my Ubuntu drives... /dev/sda7. It was fat32 drive first then I formatted it to exr3 using Gparted... after that I was able to mount but I was NOT able to copy paste anything to that drive... it said that I am NOT the ROOT user or something like that.

so I changed the mount point from properties and gave this "/"... now it gives error message saying "mount_point cannot contain the following characters: new line, G_DIR_SEPARATOR..."

after a while showing this message another message pops up like this

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I have reformatted the partition but that didn't help...

GUYS... I need your help... please help...

---

### Post by michy99 on 2009-08-12
Post the output of these commands.```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

