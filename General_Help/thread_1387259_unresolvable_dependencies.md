---
title: "unresolvable dependencies?"
date: 2010-01-21
forum: General Help
---

### Post by gwpritch on 2010-01-21
I am trying to install a copy of libexpat1-dev from the jaunty repos.

I get the following error:

```
The following packages have unmet dependencies:
  libexpat1-dev: Depends: libexpat1 (= 2.0.1-4) but 2.0.1-4ubuntu0.9.04.1 is to be installed
```

Are these not the same versions?  Now what?
Thanks

---

### Post by mc4man on 2010-01-21
not really, there looks like the was a security update.
[look here]("http://changelogs.ubuntu.com/changelogs/pool/main/e/expat/expat_2.0.1-4ubuntu0.9.04.1/changelog") and you'll see

Anyway go to System -> Admin.. -> Software Sources -> updates and make sure that the first 2 sources are enabled ( at least the first one- security

If not enabled, do so, then click close and reload.

If there were enabled then close out and in terminal
```
sudo apt-get update
```

After that you should be able to install

---

### Post by gwpritch on 2010-01-21
Right on man!  Thanks.

---

