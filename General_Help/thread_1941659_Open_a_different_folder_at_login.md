---
title: "Open a different folder at login"
date: 2012-03-16
forum: General Help
---

### Post by sd@ksu on 2012-03-16
Whenever a user log in , he/she goes to his /her home folder by default. Is there a way to change it such that his home folder still remains the same but when he/she log in , he/she goes to say $HOME/Documents.

---

### Post by jwbrase on 2012-03-16
> **sd@ksu said:**
> Whenever a user log in , he/she goes to his /her home folder by default. Is there a way to change it such that his home folder still remains the same but when he/she log in , he/she goes to say $HOME/Documents.

You could add "cd $FOLDER_YOU_WANT_TO_START_IN" to ~/.profile or ~/.bashrc (or the equivalent files for your shell if you use something other than bash).

---

### Post by codemaniac on 2012-03-16
you can use the usermod command to change the default login directory .

```
usermod -d *newdir **login_name*
```

---

### Post by jwbrase on 2012-03-16
The OP specified that he wishes to keep the same home directory, but have his working directory at login be something other than his home directory. usermod -d changes your home directory.

---

### Post by sd@ksu on 2012-03-17
Thanks to both of you...yes usemod -d changes the home directory..The cd dir thing in ~.profile works in terminal. That should be good enough for me for now.

---

