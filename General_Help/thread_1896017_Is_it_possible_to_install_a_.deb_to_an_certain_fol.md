---
title: "Is it possible to install a .deb to an certain folder?"
date: 2011-12-16
forum: General Help
---

### Post by fredand44 on 2011-12-16
Hello Guys!

I'm planning to install Oracle Express 10g:
[http://www.oracle.com/technetwork/database/express-edition/downloads/102xelinsoft-102048.html](http://www.oracle.com/technetwork/database/express-edition/downloads/102xelinsoft-102048.html)

How ever I would like to have my own applications under a specific folder like_
/home/fredrik/Applications/

Is it possible to tell the installation to be put under this folder?
(Or is this a bad idea) 

I just installed MySQL from a .deb and that installation got placed somewhare else.
I never got the chance to set the installation folder.

Best regards
Fredrik

---

### Post by thaelim on 2011-12-16
.deb files have all the installation paths built-in when they are created. The paths are determined by the distribution that the package was built on. So no, there is no way to modify these after the fact - the only way would be to download the sources for the relevant program and build it yourself to include custom paths (if its build system supports this).

---

### Post by fredand44 on 2011-12-16
Thanks for that answer!

Then I know and I see no reson why I should make it harder!!

Thanks alot!!

---

