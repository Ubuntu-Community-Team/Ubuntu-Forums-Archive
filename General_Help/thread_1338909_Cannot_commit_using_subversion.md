---
title: "Cannot commit using subversion"
date: 2009-11-26
forum: General Help
---

### Post by Koalano on 2009-11-26
Hi friends,

My OS is Ubuntu 8.04. Recently I could not commit changes from my local directory to my repository. When I type:

```
svn commit -m "some comments" ./test.cpp
```I get the error:

```
svn: symbol lookup error: /usr/lib/libaprutil-1.so.0: undefined symbol: apr_os_uuid_get
```I tried re-install libaprutil but it did not help.

So please help me to solve this problem.

Thank you very much.

Edit: Ok, so I have solved the problem. For people who also have this problem, what I did is uninstall and then reinstall apache, apr, and aprutil.

Thanks and regards,

Koalano.

---

