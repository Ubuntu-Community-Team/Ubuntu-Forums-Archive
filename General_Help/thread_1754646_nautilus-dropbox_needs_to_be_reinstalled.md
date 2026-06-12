---
title: "nautilus-dropbox needs to be reinstalled"
date: 2011-05-10
forum: General Help
---

### Post by Vinas on 2011-05-10
Just posting a strange dropbox problem with Ubuntu 10.04 x64 (in case anyone else runs into this problem). There are no solutions posted online that I could find... Please move this post if it is in the incorrect area.


An error happens when you try to install [some] program with apt. I was trying to install **cups-pdf** but dropbox messes up the install and says:

```
The package nautilus-dropbox needs to be reinstalled, but I can't find an archive for it.

```

You cannot force aptitude to remove the program, but the following worked for me:
```
sudo dpkg --remove --force-remove-reinstreq nautilus-dropbox
```


hope this helps someone out there...

---

