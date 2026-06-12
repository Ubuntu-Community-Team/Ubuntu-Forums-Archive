---
title: "portability of /etc/passwd, /etc/groups, /etc/shadow?"
date: 2009-07-24
forum: General Help
---

### Post by Pitt Stains on 2009-07-24
Hello,

I'm replacing the hard drive in my laptop.  I've installed Ubuntu on the new drive and, rather than recreate all the users and groups on the new installation, I was considering copying over /etc/passwd, /etc/groups, and /etc/shadow from the old drive to the new one.

I'm not sure how portable those files are, though, or if there are other files or considerations I should take into account.

Any thoughts?

---

### Post by sisco311 on 2009-07-24
> **Pitt Stains said:**
> if there are other files or considerations I should take into account.

Any thoughts?

/etc/gshadow 

It should work (assuming you (re)installed the same version), but 
**backup the files** before replacing them and keep a *Live CD handy*.

---

### Post by Pitt Stains on 2009-07-24
> **sisco311 said:**
> /etc/gshadow

Thanks, I'd never even noticed that file before.  Looking forward to trying this out this weekend!

---

### Post by sisco311 on 2009-07-24
> **Pitt Stains said:**
> Thanks, I'd never even noticed that file before.  Looking forward to trying this out this weekend!

btw, new users and groups are added at the and of the files.

you can use the *[diff]("http://lowfatlinux.com/linux-compare-files-diff.html")* command to compare the files line by line. 

the output should be something like:
```
diff passwd.old /etc/passwd

33,35c33
< user1:x:1002:1002::/home/user1:/bin/bash
< user2:x:1003:1003::/home/user2:/bin/bash
< user3:x:1004:1004::/home/user3:/bin/bash
---
> 

```

---

### Post by Pitt Stains on 2009-07-25
After doing a diff I decided it would be best not to try to replace these files.  There were a few cases where the two different versions of /etc/group had a different group name for a given group id.  Since these groups presumably own some of the files on the filesystem by virtue of the default installation, I foresaw all sorts of chaos ensuing from such a change.

---

### Post by bodhi.zazen on 2009-07-25
> **Pitt Stains said:**
> After doing a diff I decided it would be best not to try to replace these files.  There were a few cases where the two different versions of /etc/group had a different group name for a given group id.  Since these groups presumably own some of the files on the filesystem by virtue of the default installation, I foresaw all sorts of chaos ensuing from such a change.

Ironically, this was going to be my advice. It would be tricky at best , depending on how many users you have.

You might want to look at scripting the addition of new users. 

[http://www.howtoforge.com/user_password_creating_with_a_bash_script](http://www.howtoforge.com/user_password_creating_with_a_bash_script)

There are other examples, some more or less complex, as you wish. Some scripts force the user to change his or her password at the first log in for example =)

---

