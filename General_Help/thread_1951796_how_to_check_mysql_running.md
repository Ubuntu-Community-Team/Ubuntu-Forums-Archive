---
title: "how to check mysql running ?"
date: 2012-04-03
forum: General Help
---

### Post by winzip on 2012-04-03
how to check mysql running ?

what command to shoot ?

---

### Post by Lars Noodén on 2012-04-03
You can do it two ways:

```

# this way
status mysql

# or this way
pgrep -l mysqld

```

What version of Ubuntu are you running?

---

### Post by winzip on 2012-04-03
> **Lars Noodén said:**
> You can do it two ways:

```

# this way
status mysql

# or this way
pgrep -l mysqld

```

What version of Ubuntu are you running?

ubuntu 10 server OS

---

### Post by Lars Noodén on 2012-04-03
Ok.  Those instructions also apply to 10.10

---

