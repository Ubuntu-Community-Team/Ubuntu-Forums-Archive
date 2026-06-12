---
title: "Permissions problems"
date: 2009-10-13
forum: General Help
---

### Post by cguy on 2009-10-13
3 users want to share one's ~/.tomboy folder.

1. I created a new group named tomboy and added the three users.
2. I logged in as user A who owns the .tomboy dir and issued the command ```
chgrp tomboy .tomboy
``` and set up the permissions.
3. Then I logged in as user B who wants to access that folder and issued the command
```
newgrp tomboy
```

Within user B's terminal I have the those specified permissions, but within Nautilus I don't.
I also tried ```
newgrp - tomboy
``` but to no avail.

What's wrong?
Any suggestions that don't imply logging out and in again?

(Jaunty)

---

### Post by PriceChild on 2009-10-13
Silly thing... check that the permissions on the file/folder give the group 'tomboy' access to do whatever you want to do.

---

### Post by cguy on 2009-10-13
Checked.
I can do anything I have permissions for inside the Terminal, but not in Nautilus.

edit: and ```
ls -al
``` returns ```
drwxrwxr-x  5 george tomboy      4096 2009-10-13 23:12 .tomboy
``` whether I issue it as user A or user B.

---

### Post by diesch on 2009-10-13
You need to logout B and login again.

---

### Post by cguy on 2009-10-13
But I don't want to :(

:D
Nothing else would work?

---

