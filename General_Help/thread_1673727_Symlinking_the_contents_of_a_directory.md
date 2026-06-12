---
title: "Symlinking the contents of a directory?"
date: 2011-01-22
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2011-01-22
Hi, I'm trying to create a symlink between the contents of one folder to another folder.

```

sudo ln -s /var/log/apache2 /var/www/logs
```This works, but not in the way I intended. CDing to /var/www/logs leaves the folder apache2 that I have to CD into to see the files.

Is there a way I can link the contents of the folder, not just the folder itself?

---

### Post by Vaphell on 2011-01-22
symlinks are simply aliases that point to the same physical directory so you can't add 2 different existing directories to sum their contents.
You need to remove one of them and recreate it as a symlink to the other one.

---

