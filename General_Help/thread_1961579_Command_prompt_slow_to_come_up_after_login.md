---
title: "Command prompt slow to come up after login"
date: 2012-04-19
forum: General Help
---

### Post by nnason on 2012-04-19
Recently I upgraded my server to 11.10 and now when I log in from the command line, it takes about sixty seconds for the command prompt to appear (it immediately says "You have new mail").  This also happens when I login from another computer using ssh and when I use su to become the superuser.  Any ideas where I might look to track down this issue?

---

### Post by 2F4U on 2012-04-19
If you login to an administrative account and are told that there is mail, this is often and indication of a problem. Did you ever look into the mail? It may also be worth looking into the log files of the server and see if there are problems.

---

### Post by nnason on 2012-04-19
Yes, checked the mail and it did not have anything to do with the problem (just a notice that an avantfax port was not working).

---

