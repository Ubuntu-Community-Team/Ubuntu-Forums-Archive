---
title: "path and .profile question"
date: 2010-01-14
forum: General Help
---

### Post by rushinblue on 2010-01-14
How do I permanently add a location to my $PATH so it is always there when I open terminal?

Also is there a GUI for this?

Thanks

---

### Post by Brandon Williams on 2010-01-15
Let's say that the directory you want in your path is '$HOME/bin', then you can add the following to your ~/.profile so that it's applied in bash whenever you log in:
```
PATH="$HOME/bin:$PATH"
```

The gdm Xsession script will source your .profile if it exists, so you'll get the modified path for both terminal and X logins.

---

### Post by rushinblue on 2010-01-19
Is that by editing the ~/.profile

or just entering it @ term?

---

