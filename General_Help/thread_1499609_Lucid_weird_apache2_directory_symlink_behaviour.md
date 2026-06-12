---
title: "Lucid weird apache2 directory symlink behaviour"
date: 2010-06-02
forum: General Help
---

### Post by kenlo on 2010-06-02
There is a symlink from /var/www to a personal directory.  FollowSymlink and chmod 755 are all set.  It works perfectly until each morning I will get a "Symbolic link not allowed or link target not accessible" error.  When I do a "sudo service apache2 restart", the problem will go away.

On Karmic, it never happens.

---

### Post by kenlo on 2010-06-14
Solved.  The home directory is encfs.  So when the user logs out, apache won't be able to symlink to the directory/file.

---

