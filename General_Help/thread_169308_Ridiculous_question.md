---
title: "Ridiculous question"
date: 2006-05-02
forum: General Help
---

### Post by dschmier on 2006-05-02
I just finished installing 5.10 and I wanted to know if there is some sort of default root password or something I missed during installation.  It never gave me an option to set a root password, it only let me set a user and that user's password.  Now, X isn't working so I have to mount my windows partition in order to get the drivers for my video card but of course I can't do that unless I'm root.  I'm sure I didn't miss something during installation, so what is my root password?

---

### Post by tseliot on 2006-05-02
we use "sudo" in Ubuntu.

Try:
```
sudo name_of_the_command
```

and you'll have root permissions

If you wish, you might as well set a root account.

---

### Post by Ubuntuud on 2006-05-02
(the root password is the same as the one of the account you made during install)

---

### Post by Gustav on 2006-05-02
look at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by dschmier on 2006-05-02
Thanks, I knew there had to be a simple solution to my problem.  Now to actually go about getting my video card to work...

---

