---
title: "LVM Volume Permissions Issue"
date: 2009-07-21
forum: General Help
---

### Post by whatisthe on 2009-07-21
Background: Running latest 64bit Jaunty Desktop

I partitioned an 8TB hardware raid array using parted with a gpt table. Then I used LVM2 to create a few volumes with the ext3 filesystem. I mounted them in /dev/media and edited the /etc/fstab so that they would automount.

The problem is the volumes created seem to have root permissions and I cannot access them as a normal user. I'm not really sure how to go about changing the permissions, I'm fairly new to linux and the only permissions changing I've done is with chmod.

I've configured netatalk to allow different users to access different volumes, with many users being allowed to access a main media volume, some with read-write access and some with read-only access. I don't want to set permissions on the volumes that would not allow me to share them through netatalk with these set permissions.

Please help a new ubuntu enthusiast :)

---

