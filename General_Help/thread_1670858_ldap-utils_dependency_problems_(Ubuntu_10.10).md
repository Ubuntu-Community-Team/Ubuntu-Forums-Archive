---
title: "ldap-utils dependency problems (Ubuntu 10.10)"
date: 2011-01-19
forum: General Help
---

### Post by zhoekstra on 2011-01-19
I'm currently attempting to install the package ldap-utils, and i'm getting the following error:

```
ldap-utils : Depends: libldap-2.4-2 (= 2.4.21-0ubuntu5.3) but 2.4.23-0ubuntu3 is to be installed
```

From what I can infer, this means that the version of libldap I have is slightly more advanced than the version ldap-utils depends. If this is true, can I force ldap-utils to use the newer version as a dependency?

---

