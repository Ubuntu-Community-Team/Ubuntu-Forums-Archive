---
title: "I'm in the group but &quot;Permissions denied&quot;"
date: 2011-06-22
forum: General Help
---

### Post by kevcoder on 2011-06-22
...using 11.04

I don't understand... why does my account not have writes to this directory.  
```

dev@kevcoder00:/srv/samba/share$ groups
dev adm dialout cdrom plugdev lpadmin admin sambashare
dev@kevcoder00:/srv/samba/share$ ls -d */ -l
drwxr-xr-x 8 nobody sambashare 4096 2011-06-22 19:52 movies/
drwxr-xr-x 2 nobody sambashare 4096 2011-06-12 00:49 music/
dev@kevcoder00:/srv/samba/share$ mkdir test
mkdir: cannot create directory `test': Permission denie

```

---

### Post by jerome1232 on 2011-06-22
Have you logged out since adding yourself to that group? You will need to log out then log back in for group changes to take affect.

---

### Post by kevcoder on 2011-06-22
I should have googled first...

the group only has r-x permissions.  I ran the following and I'm good
 ```
 
sudo chmod -R g+w share

```

---

