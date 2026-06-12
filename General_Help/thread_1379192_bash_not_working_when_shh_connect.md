---
title: "bash not working when shh connect"
date: 2010-01-12
forum: General Help
---

### Post by biebo on 2010-01-12
When I connect to my PC with

```
ssh localhost
```

it says :::


Linux bibrak-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

Last login: Tue Jan 12 19:18:57 2010 from localhost

But i doesn't run the bash itself.
I have to manually run it.

```

bibrak@bibrak-laptop:~$ bash
E N V I R O M E N T      S E T 
 ---------------------------
         -------

```


How can I set it to auto
means , connect and run the bash

thanks

---

### Post by slakkie on 2010-01-12
chsh and select /bin/bash as your default shell.

Or make sure you source the correct files in your .bashrc.

---

