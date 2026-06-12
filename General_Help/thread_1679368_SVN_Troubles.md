---
title: "SVN Troubles"
date: 2011-01-31
forum: General Help
---

### Post by stunet on 2011-01-31
Hi,

I have moved my SVN over to my linux server. Trouble is, even though the directory has 777 access and I made myself and the group subversion the owners. I keep getting an error stating that the database is read-only.

adding to to the oddness, it commits anyways. Though if i happen to delete something, it keep bugging me saying its missing(even though i told it  to delete it.

does anyone know what i'm doing wrong? I really want to keep it here to avoid an extra thing to run on a remote system.

thanks :)

---

### Post by stunet on 2011-02-01
any ideas? Hate bumping a thread, but I really am stumped on this issue.

---

### Post by stunet on 2011-02-01
I found the answer to my problem :)

Here is the solution if someone else runs into the same thing:

[http://www.gsdesign.ro/blog/error-svn-attempt-to-write-a-readonly-database-commit-failed/](http://www.gsdesign.ro/blog/error-svn-attempt-to-write-a-readonly-database-commit-failed/)

---

