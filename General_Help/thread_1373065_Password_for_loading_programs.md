---
title: "Password for loading programs?"
date: 2010-01-05
forum: General Help
---

### Post by zozza on 2010-01-05
Hello,

I want to be able to password protect specific programs.  So, for example, when you click on Thunderbird a box pops up and asks for a password.

Any suggestions?  Thanks.

---

### Post by 3vi1 on 2010-01-05
Are you sure you don't really want to set up multiple accounts (or a guest account) instead?  I can't see the purpose in password protecting specific programs, unless you're going to be letting someone use your personal account - which is throwing the security handbook out the window in itself.

I suppose you could always change the permissions on the thunderbird binary and .mozilla-thunderbird directories so that your normal account doesn't have access to them, then you could change the link so that it ksudo's the binary as a different, authorized, account.  I've never tried that myself, though.

---

