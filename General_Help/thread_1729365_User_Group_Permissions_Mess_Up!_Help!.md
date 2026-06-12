---
title: "User Group Permissions Mess Up! Help!"
date: 2011-04-14
forum: General Help
---

### Post by ubila on 2011-04-14
Hello,

My main account 'dave' runs as admin etc

This was the output of 'groups dave':
dave adm dialout cdrom plugdev lpadmin sambashare admin

I was trying to add dave to the user group 'media-www'
and i ran this command: 'usermod -G media-www dave'

Then after another 'groups dave':
dave : dave media-www

It seems to have removed all the other groups!!! 
How do I restore this?

Thanks!

---

### Post by ~Plue on 2011-04-14
you'll need to re-add yourself to the groups (possibly from another user with administrative privileges or from the recovery mode)
```

usermod -G adm,dialout,cdrom,plugdev,lpadmin,sambashare,admin,media-www   dave
```for reference: usermod -G would remove you from any group that is not included in the list when you give the command (except the primary group). so f you want to to add a user to a specific group without changing the current list, you'll need to use the -a option too. or use *gpasswd -a USERNAME GROUPNAME* instead
see the man pages for usermod and gpasswd for more details

---

### Post by ubila on 2011-04-14
> **~Plue said:**
> you'll need to re-add yourself to the groups (possibly from another user with administrative privileges or from the recovery mode)
```

usermod -G adm,dialout,cdrom,plugdev,lpadmin,sambashare,admin,media-www   dave
```for reference: usermod -G would remove you from any group that is not included in the list when you give the command (except the primary group). so f you want to to add a user to a specific group without changing the current list, you'll need to use the -a option too. or use *gpasswd -a USERNAME GROUPNAME* instead
see the man pages for usermod and gpasswd for more details

This sorted out the issue!
Many thanks!

---

### Post by yetiman64 on 2011-04-14
> **ubila said:**
> This sorted out the issue!
Many thanks!

Could you mark this as solved please? Link 5 in my sig has instructions for how to, if needed.

---

### Post by ~Plue on 2011-04-14
glad it got sorted out :)
remember to mark the thread as solved

---

