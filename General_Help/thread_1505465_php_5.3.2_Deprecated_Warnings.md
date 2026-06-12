---
title: "php 5.3.2 Deprecated Warnings"
date: 2010-06-09
forum: General Help
---

### Post by pylon42 on 2010-06-09
Hello,

Since php 5.3.2 I've been seeing deprecated warnings. I'm unable to suppress them.

I've tried setting error_reporting in: 
/etc/php5/apache2/php.ini 
to:
error_reporting = E_ALL & ~E_DEPRECATED

with no success. I've also tried adding:
error_reporting(E_ALL & ~E_DEPRECATED);

... to the top of every page with no success.

I've restarted apache after each attempt.

Even setting error_reporting to "off" in php.ini has no effect. Is it possible that there's another file or setting superseding these three methods and forcing the deprecated messages to display?

Thank you in advance.

---

### Post by davidgutu on 2011-01-24
the solution is to use an earlier version of php or rewrite your code

---

### Post by CharlesA on 2011-01-24
You shouldn't use an earlier version to get around an error such as that. You should rewrite your code to use the newer method instead of the old one.

Considering the OP hasn't been back in around 9 months, this thread is closed.

---

