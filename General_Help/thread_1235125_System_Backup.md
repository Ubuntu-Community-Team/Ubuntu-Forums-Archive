---
title: "System Backup"
date: 2009-08-08
forum: General Help
---

### Post by fleamour on 2009-08-08
What Linux app can I use to back up a drive image?  Will it also backup Windows partitions?  I am currently using Acronis from within Win2k, although the Secure Zone function, kinda like a system rollback, does not function with Xubuntu installed.  But does seem to handle ext3 file systems backed up to an external drive.

---

### Post by kaibob on 2009-08-08
> **fleamour said:**
> What Linux app can I use to back up a drive image?...
I have tried various alternatives but still use Acronis True Image 10. You may want to look at Clonezilla, which is highly regarded and does back up the entire drive including Windows. 

[http://www.clonezilla.org/](http://www.clonezilla.org/)

BTW, I assume that you want to back up a hard drive not a drive image.

---

### Post by fleamour on 2009-08-09
> **kaibob said:**
> BTW, I assume that you want to back up a hard drive not a drive image.

Yeh, mixing my words.

Thanks.

---

### Post by scouser73 on 2009-08-09
> **fleamour said:**
> What Linux app can I use to back up a drive image?  Will it also backup Windows partitions?  I am currently using Acronis from within Win2k, although the Secure Zone function, kinda like a system rollback, does not function with Xubuntu installed.  But does seem to handle ext3 file systems backed up to an external drive.

Look here for backing up, i use this program and it's a very handy piece of software - [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html").

---

### Post by Barafu Albino Cheetah on 2009-08-09
Use dd. It supports everythinf because works on byte level. After that tar the image and be happy.

---

