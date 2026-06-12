---
title: "Backup system files as normal user Deja Dup?"
date: 2012-10-08
forum: General Help
---

### Post by Azrael84 on 2012-10-08
Hi,

I would to give a normal (no sudo) user the privileges to backup (but not modify) system files like /etc and so on. Deja dup haults on this as it says no permissions. Is there a way to create a group of users say 'backupers' that can do this, then add the desired user to it?

Maybe then one could edit visudo, adding a line that allowed the user group to do this without password?  Something like the following?

```

# Users in the backupers group are allowed to run back as root. 
%backupers ALL=(root) NOPASSWD:/usr/bin/cp 
```

---

### Post by Azrael84 on 2012-10-08
anyone know? there is a backup group I noticed can this be used to do it?

---

### Post by HiImTye on 2012-10-08
there's really no reason to give permissions to those files, unless you modify them yourself, in which case you can change the permissions of that file to allow others to read it using:
```
sudo chmod a+r file
```(for all users)
or```
sudo chmod o+r file
```(for 'other' users - people who aren't owners or members of the owner group of the file)

you could also add those people to the group that owns the file (and set the group of the file to something other than *root*)
```
sudo chgrp *group file*
sudo usermod -a -G *group user*
```

---

### Post by Azrael84 on 2012-10-09
Thanks,

I want it so that the normal user can only read and copy the directory, not modify it. Wouldn't giving them ownership allow them to do whatever with the system files?

---

### Post by HiImTye on 2012-10-09
yes, so just use one of the first two options, using chmod
well, not necessarily, you can set 'group' permissions separately, but if you just want a one liner, use one of the other ones

for using group, without write permissions
```
sudo chgrp *group file*
sudo chmod g=rX *file*
sudo usermod -a -G *group user*
```

---

### Post by Azrael84 on 2012-10-09
thanks, so is it not sufficient to have read permissions to copy a file? even if I'm gonna write it in my home directory say?

---

### Post by HiImTye on 2012-10-09
it is sufficient to have read permissions, but some files that you may want to copy also have the execute flag, so it will preserve the flag if it exists. I'm not sure how it would work copying a file that has the execute bit set if you don't have execute permissions, it might remove the execute bit, forcing you to have to set it manually. it's up to you, really, I was just thinking ahead to other problems. generally you shouldn't need to copy anything outside of /home/ or your storage directories, anyway. this whole situation is rather strange.

---

