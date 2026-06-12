---
title: "execute cmd with secondary group"
date: 2009-07-30
forum: General Help
---

### Post by heluani on 2009-07-30
Hello, how should be the sudoers entry to allow 

sudo -u user -g group command

where group is a secondary group for user?

now I have my user in the admin group and an entry```

%admin ALL=(ALL) NOPASSWD:ALL
```
but still I get ```
Sorry, user "user" is not allowed to execute "command" as "user:group" on "host"
```

related question, how can I run command with a secondary group as a my gid?

R.

---

### Post by heluani on 2009-07-30
disregard, I didn't realize that 

user ALL=(user:group)NOPASSWD:ALL

would do

---

