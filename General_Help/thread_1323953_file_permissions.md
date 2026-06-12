---
title: "file permissions"
date: 2009-11-12
forum: General Help
---

### Post by Dithers on 2009-11-12
Is there any way to force all files and directory's created in a specific directory to inherit the group ownership from the parent directory.

as it is now my wife and I both upload pictures from our cameras to a directory called photos, all photos in the directory belong to the group
photos, but when we upload a new directory of pictures, the other has no access until I chgrp -R the directory. since whoever uploaded, is both owner and group

the files hold on to the 770 permissions, but not the group. which makes the permission useless.

---

### Post by sisco311 on 2009-11-12
> **Dithers said:**
> Is there any way to force all files and directory's created in a specific directory to inherit the group ownership from the parent directory.

as it is now my wife and I both upload pictures from our cameras to a directory called photos, all photos in the directory belong to the group
photos, but when we upload a new directory of pictures, the other has no access until I chgrp -R the directory. since whoever uploaded, is both owner and group

the files hold on to the 770 permissions, but not the group. which makes the permission useless.

set the [setgid]("http://en.wikipedia.org/wiki/Setuid#setgid_on_directories") permission on the directory:
```
chmod g+s /path/to/dir
```

---

