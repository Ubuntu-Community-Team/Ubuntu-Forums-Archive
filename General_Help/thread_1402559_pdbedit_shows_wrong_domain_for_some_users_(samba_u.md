---
title: "pdbedit shows wrong domain for some users (samba using tdbsam)"
date: 2010-02-09
forum: General Help
---

### Post by semi-newbie on 2010-02-09
Using Ubuntu 9.10, Samba 3.4.0 (pdbedit -V outputs "Version 3.4.0"), and tdbsam.

The command

    pdbedit -v -L | less

lets me see various information about each windows login account that is set up.

I was able to use

    pdbedit -u username -f "New Fullname"

to change the full name of a few users.

However, there are also three cases where instead of the proper domain name being used, there is an incorrect domain name listed.  I would like to fix this problem, but there is no option similar to "-f" that will allow me to specify the proper domain name.

Can anyone tell me how to change the listed domain name?

---

