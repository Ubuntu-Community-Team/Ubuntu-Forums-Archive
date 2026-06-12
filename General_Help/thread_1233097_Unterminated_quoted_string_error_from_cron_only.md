---
title: "Unterminated quoted string error from cron only"
date: 2009-08-06
forum: General Help
---

### Post by didier9 on 2009-08-06
I have a set of Perl scripts that run fine from the command line, but they generate an error message or warning "Unterminated quoted string" only when run from crond. I get these messages in my mail every day.

The scripts generate index files to speed searches from cgi-scripts. They normally only need to run once a day, at night. In spite of that message, the scripts actually do their job and complete. It may be an issue of the scripts returning a bad code to crond, but these are just Perl scripts that print a one liner to the standard output and terminate with exit.

I run Ubuntu 9.04

I do not know how to troubleshoot this since the scripts run fine from the command line.

I had similar scripts running fine under Ubuntu 8.0.

Any suggestion gladly accepted...

Thanks in advance

Didier

---

### Post by didier9 on 2009-08-06
OK, as usual, after posting my question, I found the *stupid* error...
Sorry for the bandwidth...

Didier

---

