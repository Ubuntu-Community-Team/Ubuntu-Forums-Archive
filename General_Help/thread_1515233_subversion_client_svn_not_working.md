---
title: "subversion client svn not working"
date: 2010-06-22
forum: General Help
---

### Post by shri_nath on 2010-06-22
Hello,
I recently installed the Ubuntu 10.04 Desktop (x86_64 GNU/Linux).
And then installed the subversion package.
Now I cannot checkout the source-code repositories. I get the following error message:

```
[I]$ svn co [https://svn.sourceline.com/biller/trunk](https://svn.sourceline.com/biller/trunk)
**svn: Unusable URI: it does not refer to this repository**[/I]
```
But note that both of the following work:

```
*$ svn list [url]https://svn.sourceline.com/biller/trunk[/url*
```
as well as
```
*$ svn export [https://svn.sourceline.com/biller/trunk/pom.xml](https://svn.sourceline.com/biller/trunk/pom.xml)*
```

This used to work on the Ubuntu 9.10. Any help will be appreciated.
Thanks.

-sn

---

