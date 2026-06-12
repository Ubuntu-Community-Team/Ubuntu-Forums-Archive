---
title: "Postfix mail forwarding through yahoo"
date: 2011-05-01
forum: General Help
---

### Post by doctordruidphd on 2011-05-01
I am currently using msmtp to forward outgoing mail through yahoo, where I have an account.  I would like to use postfix instead, and set it up to do the following:

1. Mail addressed to users on the system should go directly to them, not through yahoo.

2. Mail addressed to a specific address (specifically [email]username@winlink.org[/email]) should be sent to a special processing program. The instructions I found for doing this are here:
[http://groups.yahoo.com/group/paclink-unix/message/331](http://groups.yahoo.com/group/paclink-unix/message/331)
but following them crashes postfix completely.

3. General internet mail (username@what.ever.com) should be forwarded through yahoo.

Postfix is currently doing (1) just fine, all of my attempts to do either 2 or 3 just crash it. Any ideas how to proceed?

---

