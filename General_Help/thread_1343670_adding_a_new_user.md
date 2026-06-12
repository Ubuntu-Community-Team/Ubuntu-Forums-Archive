---
title: "adding a new user"
date: 2009-12-02
forum: General Help
---

### Post by ShayHP on 2009-12-02
sorry about the noob question
but i couldn't add a user.
how to do it?

---

### Post by endBc on 2009-12-02
```
sudo adduser sister

```

As you run it in command line, it doesn't matter what Ubuntu flavor you are running.

---

### Post by fancypiper on 2009-12-02
You have to create a new user as root.

Command line:
sudo useradd <username>
Follow the prompts.

Gnome GUI:
System>Administration>Users and Groups

---

### Post by ShayHP on 2009-12-07
i created a user but then deleted it with the command sudo deluser <user>
now i'm trying to add another instead but i don't get a password prompt.
it just adds the user and then when i try to log on it asks for a password which i didn't entered.

help?

---

