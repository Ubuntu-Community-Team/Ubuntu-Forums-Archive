---
title: "Zeitgeist crashed at startup"
date: 2011-05-12
forum: General Help
---

### Post by Y_Ernst on 2011-05-12
This bug is already reported several times in launchpad.

The Zeitgeist Daemon crashes at startup and my day starts with a zombie hunt.

```

ps -A | grep defunc
1722 ?        00:00:00 zeitgeist-datah <defunct>

```

This happens to all my 64-bit systems.

clearing the sqlite database or reinstalling the package doesn't help.

By the way: Why doesn't Zeitgeist use Couch-DB?

---

