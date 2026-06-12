---
title: "delete failed to free disk space"
date: 2010-09-15
forum: General Help
---

### Post by iapx86 on 2010-09-15
My 221G ext4 disk was 97% full.
In nautilus I deleted a 20G directory.
My disk is still 97% full.
How do I get the 10% more free space back?

---

### Post by Achilles124 on 2010-09-15
Take a look at this post:
[http://ubuntuforums.org/showthread.php?t=1342807]("http://ubuntuforums.org/showthread.php?t=1342807")

When you want to delete something permanently it is best to run nautilus in root: gksudo nautilus

Then remove the files with: Shift+ Delete. Don't forget the Shift.

Look for the files you have deleted but still are on your system under:
.root/local/share/trash/files

---

### Post by Gunman1982 on 2010-09-15
Did you empty the trash bin?

---

### Post by Gunman1982 on 2010-09-15
> **Achilles124 said:**
> Take a look at this post:
[http://ubuntuforums.org/showthread.php?t=1342807]("http://ubuntuforums.org/showthread.php?t=1342807")

When you want to delete something permanently it is best to run nautilus in root: gksudo nautilus

Then remove the files with: Shift+ Delete. Don't forget the Shift.

Look for the files you have deleted but still are on your system under:
.root/local/share/trash/files

There is normally no need to do that with root priviliges. 

The shift+Delete option is available to normal user too.

---

### Post by iapx86 on 2010-09-15
Thank you.):P

I found the deleted files in: /root/.local/share/trash/files

Now I will attempt to delete them completely.
Please tell me a reason why I ought not use: rm -fr {UnwantedFiles}

Update: That works perfectly.  Thanks to all.

---

### Post by Drigomaniac on 2010-09-15
Just ti check whats occupying more space, typy sudo du -sh *

---

### Post by philinux on 2010-09-15
Also see this.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

