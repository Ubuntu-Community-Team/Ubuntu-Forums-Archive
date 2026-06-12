---
title: "Automatic mounting of a second hard drive on bootup"
date: 2009-10-30
forum: General Help
---

### Post by alan_uk on 2009-10-30
I have just installed 9.10 and have a second hard drive (formatted ext4) for storage (Computer/ Filesystem/ media/ f80467b3-dc02-419e-ae1b-9df4a9facc12). Is there a way to make this second hard drive mount automatically on boot up without having to go to the Places Menu, and then authenticate.

Thanks
Al

---

### Post by unmole on 2009-10-30
Try installing pysdm from the repos

---

### Post by The Cog on 2009-10-30
pysdm is a gui that should allow you to configure that.

It you want to know the gory under-the-hood details, you need to do two things:
Firstly create a directory for the disk contents to appear in (known as a mount point). Traditionally this would be a directory inside the /mnt directory. If you choose to make a directory inside /media instead, then I think the contents will appear on your desktop, but I think /media is really intended for removable media.

Secondly, add a line like this one to the file /etc/fstab (substitude the correct mount point, the directory you just created):
UUID=f80467b3-dc02-419e-ae1b-9df4a9facc12 /mnt/seconddrive ext4 defaults 0 2

---

### Post by alan_uk on 2009-10-30
Thanks for the help - works good

al

---

