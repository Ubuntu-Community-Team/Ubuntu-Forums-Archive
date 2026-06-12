---
title: "Software Centre problem"
date: 2010-04-02
forum: General Help
---

### Post by cosmosboy on 2010-04-02
I ran update manager earlier and since then I can't access the software centre - I get an error message:

[B]Sorry, can not open the software database.
Please re-install the 'software-center' package.[/B]

I can't figure out how to fix the problem. Any help would be much appreciated.

---

### Post by CompyTheInsane on 2010-04-02
> **cosmosboy said:**
> [B]Sorry, can not open the software database.
Please re-install the 'software-center' package.[/B]


Given the error message, you can run
```

sudo apt-get install --reinstall software-center

```
to reinstall it.

---

### Post by cosmosboy on 2010-04-02
Many thanks.

---

