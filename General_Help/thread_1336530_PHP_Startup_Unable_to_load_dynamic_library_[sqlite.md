---
title: "PHP Startup: Unable to load dynamic library [sqlite3 error]"
date: 2009-11-24
forum: General Help
---

### Post by deselect on 2009-11-24
Please see this thread for a general explanation of my issue: [https://bugs.launchpad.net/ubuntu/+source/php-sqlite3/+bug/281714](https://bugs.launchpad.net/ubuntu/+source/php-sqlite3/+bug/281714)

Error mentioned above:

```

PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite3.so' - /usr/lib/php5/20060613+lfs/sqlite3.so: cannot open shared object file: No such file or directory in Unknown on line 0
No syntax errors detected in test.php

```

The problem I am facing and desparately hoping someone can help me with is this: when I do as suggested in the link above, it fixes the PHP specific problem and all seems fine. However, upon restarting my PC, it seems any program that requires sqlite3 hangs indefinitely (Evolution, etc.)

Has anyone found a proper fix to this? I am a Web developer, so I really must have it fixed right.

Thanks in advance,

A

---

### Post by deselect on 2009-11-25
Bump?

---

