---
title: "Bash grep and a variable?"
date: 2009-07-07
forum: General Help
---

### Post by Hawk__0 on 2009-07-07
Is it possible to do this?
I am trying to get user input, which is a string that will be used for grep but it doesn't seem to be working.

This is the command I'm using:
ps -ef | grep "\$search$" | less

---

### Post by sedawk on 2009-07-07
```

> export search=firefox
> ps -ef |grep "$search$"
user      6756     1  5 22:34 ?        00:03:02 /usr/lib/firefox-3.0.11/firefox

```

But try "pgrep" which does ps+grep:
```

> pgrep $search

```

---

### Post by Hawk__0 on 2009-07-07
Thanks for the reply.  pgrep doesn't have the options I want.  Also $search$ seems to retrieve EVERYTHING, regardless of what I enter.

---

