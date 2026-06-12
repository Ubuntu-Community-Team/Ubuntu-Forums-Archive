---
title: "rsync creating wrong permissions?"
date: 2010-05-01
forum: General Help
---

### Post by johann_p on 2010-05-01
I try to use rsync for backing up some directories and I have to following problem: some files have permissions that prevent me from running rsync under my own user id. So I run it under root using the option "-a" which according to the man page should preserve the permissions, owner and group information:

However, when I run this under root, the directories created in the backup location get user root and group root while ordinary files keep the original user and group. 

What am I missing here? How can I get rsync to preserve the user and groups for all files, including directories?

Here is a command to illustrate my problem
```

sudo rsync -a /home/youruser /tmp

```

If you try that and terminate with Ctrl-C after a few seconds, there will be a directory /tmp/youruser where the directories contained within are owned by root group root.

---

### Post by fyo on 2010-05-01
> **johann_p said:**
> If you try that and terminate with Ctrl-C after a few seconds, there will be a directory /tmp/youruser where the directories contained within are owned by root group root.

Then DON'T terminate ;)

Seriously, terminating early is a bad solution and a bad way to test anything.

Try on a more manageable folder first.

What happens is that rsync creates the folders first (with default permissions of user running rsync) and then subsequently chmod's them.

IOW: Let it finish and all should be right in the world. But, like I said, try on a more manageable folder first to make sure ;)

---

### Post by johann_p on 2010-05-01
> **fyo said:**
> Then DON'T terminate ;)


Good point and good advice, thanks :)

How it happened was that i wanted to do a real huge backup and checked while it was working if everything is going fine ... and detected all those directories owned by root. So I panicked and thought I am doing it wrong. My test using Ctrl-C just seemed to confirm this.

From a smaller test as you suggested, I could see that eventually the owner and group of the directories get adjusted too.

---

