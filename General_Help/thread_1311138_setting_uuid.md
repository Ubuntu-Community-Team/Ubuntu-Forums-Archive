---
title: "setting uuid"
date: 2009-11-02
forum: General Help
---

### Post by rgrig on 2009-11-02
The upgrade to Ubuntu 9.10 made the system un-bootable because the UUID for the root partition disappeared. Of course, I can boot using the /dev/sdX form, but I'd like to set back the old UUID. The command
```
sudo tune2fs /dev/sda1 -U <my-old-uuid>
```
seems to succeed, because
```
  sudo tune2fs -l /dev/sda1
```
prints the UUID (among lots of other stuff); it also seems to not succeed because
```
  sudo blkid -c /dev/null /dev/sda1
```
doesn't print anything. Also, the directory /dev/disk/by-uuid doen't contain the UUID I just set (even after reboot). Even worse, it seems to not succeed also because I can still boot only from /dev/sda1, but not by UUID.

So, how is it possible that "tune2fs -l /dev/sda1" always reports the uuid I expect (the last one set with "tune2fs -U" or none if the last time I cleared it), but blkid never sees the UUID I set with tune2fs?

---

