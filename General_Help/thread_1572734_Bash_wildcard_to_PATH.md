---
title: "Bash wildcard to PATH"
date: 2010-09-11
forum: General Help
---

### Post by ocirne94 on 2010-09-11
Hello all,
I have some programs compiled into /opt/programname, and I would like to be able to execute them without typing the full path; I've tried with PATH=$PATH:/opt/*/bin, but with no luck; any ideas?
Thanks!

---

### Post by WorMzy on 2010-09-11
I personally make symlinks to the executables in /usr/local/bin and add ```
PATH=$PATH":/usr/local/bin"
``` to /etc/environment (or just append it to the existing PATH declaration if there is one and doesn't already have /usr/local/bin in it)

You can make symlinks like this:

```
ln -s /path/to/executable /usr/local/bin
```

Once the link is created, you'll be able to use the application as though it was installed normally. Oh, and you make the symlinks in /usr/local/bin because that directory is empty by default, so you don't need to worry about overwriting another program's executable/symlink (of course, if you had two executables with the same name in different locations, Ubuntu will only use the first one it comes to while searching each PATH directory in turn, so try to make sure each executable/symlink has a unique name to avoid confusion).

---

### Post by Nytram on 2010-09-11
You might want to consider creating a **bin** directory in your home and putting them there. When you next login that folder will be added to your PATH automatically and the contents will execute from any location.

---

### Post by jamesisin on 2010-09-11
I put copies of my scripts in /usr/local/bin and that's that.  This is similar to what WorMzy proposes, but a) I can continue to develop those scripts without effecting the 'published' versions and b) the scripts are available to all users of the system.

The proposal by Nytram will only work for the user in question.

---

### Post by CharlesA on 2010-09-11
> **Nytram said:**
> You might want to consider creating a **bin** directory in your home and putting them there. When you next login that folder will be added to your PATH automatically and the contents will execute from any location.
Interesting.

Thanks for the info!

---

