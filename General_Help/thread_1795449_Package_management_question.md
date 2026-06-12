---
title: "Package management question"
date: 2011-07-02
forum: General Help
---

### Post by warrenfalk on 2011-07-02
According to [http://www.debian.org/doc/debian-policy/ch-relationships.html#s-virtual](http://www.debian.org/doc/debian-policy/ch-relationships.html#s-virtual)

I should be able to do this in my debian control file:

Provides: libffado2
Conflicts: libffado2
Replaces: libffado2

And my package should then be an alternative to the libffado2 package from the repositories.  However, this doesn't work.

After my package is installed, any attempt to install something that depends on libffado2 will REMOVE my package and install the libffado2 from the repositories?

Why would it do that, and is there a way to stop it?

---

