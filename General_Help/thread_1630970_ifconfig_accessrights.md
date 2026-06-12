---
title: "ifconfig access/rights"
date: 2010-11-26
forum: General Help
---

### Post by sr_guy on 2010-11-26
I want a non-root user on my system to be able to ifconfig eth0 up/down without using sudo or root to be able to take the interface up/down. How do I go about changing those rights for a non-root user?

---

### Post by bodhi.zazen on 2010-11-26
> **sr_guy said:**
> I want a non-root user on my system to be able to ifconfig eth0 up/down without using sudo or root to be able to take the interface up/down. How do I go about changing those rights for a non-root user?

Best method is with sudo.

One of the advantages of sudo is it allows very fine grained control.

So you can configure sudo to allow access to only some commands, in your case ifconfig (or what you need).

See:

[https://help.ubuntu.com/community/Sudoers#User%20Specifications](https://help.ubuntu.com/community/Sudoers#User%20Specifications)

[http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

Set up a command alias and give your user access.

The other option would be to learn how to use acl lists.

---

