---
title: "SecurityException when running applet on firefox"
date: 2010-03-25
forum: General Help
---

### Post by okuryazar on 2010-03-25
I would like to run an applet on firefox 3.6 on ubuntu 10.4. 
and I start firefox with sudo on commandline to see the java console output.
My appplet code changes some policies and it works fine on windows. But on ubuntu I get this error:

```
java.lang.SecurityException: Changing the SecurityManager is not allowed.
    at net.sourceforge.jnlp.runtime.JNLPSecurityManager.checkPermission(JNLPSecurityManager.java:267)
    at java.security.Policy.setPolicy(Policy.java:256)
```

Is there a way to get around this problem? I saw on some other thread that adding -nosecurity on javaws helps. But I don't know how I can apply something like this on firefox.

Thank you very much

---

