---
title: "Get FTP to show up in file browser"
date: 2010-07-21
forum: General Help
---

### Post by Chiggins on 2010-07-21
Alright, so I got my FTP added under Places, figured that would be the best way to go. But, when I open a program such as Zend Studio or Eclipse to create a new project from existing source, I can't get to my FTP.

[Image here]("http://chigstuff.com/ftp_help.png")

How could I get my FTP to show up right under "System Reserved"?

Thanks!

---

### Post by bigfatgooglefat on 2010-07-22
what i would do is create a bookmark out of the FTP server folder under /$home/.gvfs/"ftp share name"

it's more of a temporary fix because it won't auto login or recreate the share after a reboot, but it's way easier than messing with a permanent mount through fstab or something similar.

hope that helps!

---

