---
title: "Add sudo user"
date: 2011-10-08
forum: General Help
---

### Post by shashanksingh on 2011-10-08
I have this problem in my lab. Some senior was the first user(and by default the sudo user) in a lab machine. Ubuntu 10.4

I had to use the machine, so I went into recovery mode-> drop to root shell. There I added myself as a new user using the useradd command, then I thought maybe changing my group to 1000 in the passwd and group files may just make me a sudoer.

But after making those two changes, it still says Im not a sudo user.

Whats the way to add myself as a sudoer by just dropping in to the root shell and using the command line??

---

### Post by jazzon on 2011-10-08
I cant walk you through this directly, but i can point you the right direction.  Since you can get to a root shell, add yourself to the 'adm', 'admin', and 'sudo' (if it exists) groups.

That might help.  Also use man pages for sudoers to look up settings for the sudo config file.

```
man sudoers
```

BE VERY VERY CAREFUL IN THAT FILE!  One typo can louse you up permanently!

---

### Post by Elfy on 2011-10-08
Get them to add you.

Sounds like circumventing policy.

Closed.

---

