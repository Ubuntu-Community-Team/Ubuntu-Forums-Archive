---
title: "Command Permissions"
date: 2010-08-18
forum: General Help
---

### Post by fasuke on 2010-08-18
I want to know: how do 1 stops a user from using some commands. If I say that there is a user named xyz, and i dont want him to use the rm or cp, how do i do that?

---

### Post by sanderd17 on 2010-08-18
you can stop him from using cerain files (or only read them) with user restrictions:

[http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php]("http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php")

If you let the user edit a file, it's the same like letting him use the rm command, he can just edit the file in a way he deletes everything.

If you could disable the rm command, a lot of programs wouldn't work anymore, a lot of programs make temp files that need to be deleted.

Do you see the problems?

Try to say what you want to do if you can't find the solution.

---

### Post by bodhi.zazen on 2010-08-18
> **fasuke said:**
> I want to know: how do 1 stops a user from using some commands. If I say that there is a user named xyz, and i dont want him to use the rm or cp, how do i do that?

1. With linux permissions - first line of defense. One can not remove files they do not own.

2. If you need more then that, you will need to look at apparmor.

---

