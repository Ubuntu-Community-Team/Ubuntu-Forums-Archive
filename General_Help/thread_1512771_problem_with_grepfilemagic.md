---
title: "problem with grep/file/magic?"
date: 2010-06-18
forum: General Help
---

### Post by gonzo1948 on 2010-06-18
Something has changed on my 8.04 ubuntu from yesterday and I do not know what (how many times have you heard that?)

Now, when ever I do this:

grep ERROR /var/log/syslog

I get this:

Binary file /var/log/syslog matches

When I do this:

file /var/log/syslog

I get this:

/var/log/syslog: data

For some reason grep is interpreting my syslog file as a data file and not as an ASCII file.  Yesterday, it was an ASCII file and grep worked fine but today it is a data file.  I hate gremlins!!!

Any ideas on how to fix this??

-Andres

---

### Post by gonzo1948 on 2010-06-18
thanks anyway...I found my problem.

/var/log/syslog had some non-ASCII chars in it and that was causing the problems.

-Andres

---

