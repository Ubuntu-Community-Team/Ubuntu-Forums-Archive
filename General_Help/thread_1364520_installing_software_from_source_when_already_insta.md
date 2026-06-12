---
title: "installing software from source when already installed with apt"
date: 2009-12-26
forum: General Help
---

### Post by jake55 on 2009-12-26
I wondering what would happen if you were to configure && make && make install a package that you alreay have installed by apt-get. This may be a different version thatn what you may have installed. How would other software that relied on some of those libraries react? is it usually ok?

Thanks

---

### Post by taurus on 2009-12-26
It depends where the compiled version gets installed.  If it's on the path that happens to be before the apt-get version, then it will be executed.  But if it's on the path behind the apt-get version (usually in /usr/bin), then your new compiled version will not be executed unless you exclusively specify it, using the full path.

---

### Post by jonest1 on 2009-12-26
I've been in the same situation and usually specify /usr/local in the configuration step.  Some people will also specify a path in their home directory to ensure separation from the previously installed version.

One way to make sure you are calling the right program is to enter the full path to the application (ie: /usr/local/bin/binary).

If you want to look at your path order, type 'echo $PATH' and first come first serve.

---

