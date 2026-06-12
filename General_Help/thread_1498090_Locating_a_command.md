---
title: "Locating a command"
date: 2010-05-31
forum: General Help
---

### Post by Ruddles on 2010-05-31
Long story short, I decided it was time to install something from source rather than just using repositories all the time.  I picked on ruby, downloaded the tar, configured, ran make, and everything went fine and dandy.  I can run "ruby -v" and get the output I expect.

My question is, how can I find out where the command "ruby" actually points to?

---

### Post by drs305 on 2010-05-31
Generally in linux you can use the "which" command to find the executable and the "whereis" command to find the files.
Examples of "which <appname>" and "whereis <appname>"
```
which gimp
whereis gimp
```

---

### Post by Ruddles on 2010-05-31
Perfect, exactly what I was after.  Much appreciated.

---

