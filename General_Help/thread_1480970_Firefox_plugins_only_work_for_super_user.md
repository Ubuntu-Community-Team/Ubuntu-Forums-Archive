---
title: "Firefox plugins only work for super user"
date: 2010-05-12
forum: General Help
---

### Post by Iudico on 2010-05-12
I'm running Ubuntu 10.04 minimal with Openbox; far from a standard install but nearly everything works the way it should.

The problem appears quite simple:

Firefox does not recognise installed plugins (i.e, Flash) when running as the standard user; if I run the command 'sudo firefox' however, Firefox loads in plugins just as it should.

I've checked about:plugins in both instances and this has confirmed what is stated above.  The list is populated when running as the super user, and empty when running as standard.

I've trawled Google for three days attempting to solve this issue but it's the only one so far that has gotten the better of me.

Assistance is appreciated; a fix would be freaking awesome. :)

---

### Post by Iudico on 2010-05-15
Well, it seems the fix was simple.  Isn't it always?

The permissions for /usr/lib/mozilla had, somehow, been set as 500, thus not allowing standard user accounts access to the plugins directory contained within; a quick 'sudo chmod -R 755 /usr/lib/mozilla' and all is well. :)

---

