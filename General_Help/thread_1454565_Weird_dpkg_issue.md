---
title: "Weird dpkg issue"
date: 2010-04-14
forum: General Help
---

### Post by TheNessus on 2010-04-14
10.4 KDE.

trying to install or remove anything results in an error:

dpkg: parse error, in file '/var/lib/dpkg/available' near line 6374 package 'apt':
 `Depends' field, reference to `libgcc1': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

any help will be appreciated much!

---

### Post by drs305 on 2010-04-14
Try running this to clear the error in the dpkg 'available' file:
```
sudo dpkg --clear-avail
```

There is a file in the same folder called "available-old", which you could copy to "available" to see whether or not it contained the same error.

---

### Post by TheNessus on 2010-04-14
> **drs305 said:**
> Try running this to clear the error:
```
sudo dpkg --clear-avail
```

Yes it solved it. Thank you wholesome!

---

