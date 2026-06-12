---
title: "Ubuntu wont log in"
date: 2012-09-13
forum: General Help
---

### Post by Zach1928 on 2012-09-13
Ubuntu 12.04 just started giving me problems. It worked before while I was in class and not it will not log in. It takes me to a screen requiring a password which it didn't do before, and it accepts the password and then goes back to the login screen. I have no idea what may have went wrong, although before my battery light came on for like 5% charge yet Ubuntu said I had over an hour of battery left which wasn't true.

Thanks in advance

---

### Post by Bashing-om on 2012-09-13
hi ! zack, Welcome to the forum.

What you are booting into is a command line terminal..After you login (username->password) what results when this is entered into this same terminal:
```

sudo service lightdm start

```Be advised the use of sudo requires your password.

Will see what can be done to restore the gui interface.
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Zach1928 on 2012-09-13
Hahaha funny story... I actually just deleted the partitions and started from scratch. Thanks though, I wish I had seen this sooner

---

### Post by Bashing-om on 2012-09-13
Long as the story has a happy ending!

[INDENT]enjoy ubuntu <==BDQ
[/INDENT]

---

