---
title: "libexpat problem"
date: 2010-02-13
forum: General Help
---

### Post by shariefbe on 2010-02-13
Hello,
   I am getting some error when i compile cross compile "dbus-1.2.20".
error
```

checking for XML_ParserCreate_MM in -lexpat... no
configure: error: Could not find expat.h, check config.log for failed attempts


```
so i downloaded te expat library sources i cross compiled. But again i am getting same error. I think i have to add "-lexpat" in LDFLAG. But i dont know how to do that. Can anyone help me?

---

### Post by shariefbe on 2010-02-15
i am struggling from last 2 days with this error. can anyone help me

---

### Post by TRDJunkie on 2011-01-14
I'm having the same problem. Can anyone help? Please :(

---

### Post by ratin3 on 2011-07-18
Same problem while compiling fontconfi-2.1.90 - I have expat.h installed in /usr/include but if I use --with-expat-includes="/usr/include/" as part of config options, it still cant find it!

---

