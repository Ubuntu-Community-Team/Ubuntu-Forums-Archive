---
title: "Copy desktop settings?"
date: 2011-03-30
forum: General Help
---

### Post by sr_guy on 2011-03-30
Ubuntu 10.04 64-bit

What is the easiest way to copy desktop settings? I want to remove a user from my system, and create a new user, but I want the same desktop setup as the user I am removing (i.e. program icons on the desktop and on the panel). That will save me the time and effort of setting it up from from scratch for the new user.

---

### Post by TeoBigusGeekus on 2011-03-30
Just backup his .home folder.

---

### Post by sr_guy on 2011-03-30
Hmmm, I didn't think it was that straight forward.

So, just...

tar -cvvf /home/username/ foo.tar

Then overwrite the new user's content inside the their home dir?

---

### Post by Karlchen on 2011-03-30
Hello, sr_guy.
> tar -cvvf /home/username/ foo.tarHm, should it not be the other way round? ```
tar -cvf /full/path/to/foo.tar /home/username
```(cf. "man tar", please.)
> Then overwrite the new user's content inside the their home dir?Hm, basically yes. But it may be a good idea to check the content of the restored configuration files for occurrences of the old username and replace them by the new username, provided the two names differ.

Kind regards,
Karl

---

