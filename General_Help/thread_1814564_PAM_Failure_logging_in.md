---
title: "PAM Failure logging in"
date: 2011-07-29
forum: General Help
---

### Post by fuzzy29 on 2011-07-29
Hi there,
When I try to login to my Ubuntu Server, I get the following error:

**PAM Failure, aborting: Critical error - immediate abort**

This occurs when I try to log in locally, or via SSH.
I have tried logging in using every account, and all create the same error.
Any help to solve this would be greatly appreciated.

**Ubuntu server edition 11**

Many thanks in advance, Daniel.

---

### Post by galvatron408 on 2011-07-29
sounds like your pam configuration is messed up. you're going to have to boot in to single user mode and fix it.

Here's a pam tutorial I found.

[http://content.hccfl.edu/pollock/AUnix2/PAM-Help.htm](http://content.hccfl.edu/pollock/AUnix2/PAM-Help.htm)

Good Luck.

---

