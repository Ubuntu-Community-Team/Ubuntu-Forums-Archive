---
title: "Adding a user, password problems"
date: 2010-03-12
forum: General Help
---

### Post by sixthwheel on 2010-03-12
I tried to add my wife , and when I put in a password for her, this error comes up.
"Please set a valid user name consisting of a lower case letter followed by lower case letters and numbers."

I did all that and I still can't set a password for her.

---

### Post by wojox on 2010-03-12
You did it like:

Giving her a home directory and substitute myuser for your wifes username

```
sudo useradd -m myuser
```

Then set the password

```
sudo passwd myuser
```

---

### Post by sixthwheel on 2010-03-12
Thank You.

---

### Post by wojox on 2010-03-14
Welcome

---

