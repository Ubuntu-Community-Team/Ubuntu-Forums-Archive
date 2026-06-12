---
title: "How to encrypt a string of text?"
date: 2009-10-08
forum: General Help
---

### Post by keenboy on 2009-10-08
Hello,

I used to have access to a server (gentoo) which had a tool called mkcrypt. We could run:

```
mkcrypt stringoftext
```

and it would output the encrypted version of the that string. We used to use it to encrypt passwords to store in a mysql database for use with nss athentication.

I now run the MySQL database on an Ubuntu system. Is there a similar tool which I can run to encrypt a string of text on the command line?

Thanks,

---

### Post by scragar on 2009-10-08
Look into Mcrypt or MySQLs built in encryption functions.

[http://dev.mysql.com/doc/refman/5.1/en/encryption-functions.html](http://dev.mysql.com/doc/refman/5.1/en/encryption-functions.html)

---

### Post by keenboy on 2009-10-08
Thanks scragar.

> Look into Mcrypt or MySQLs built in encryption functions.

[http://dev.mysql.com/doc/refman/5.1/...functions.html](http://dev.mysql.com/doc/refman/5.1/...functions.html)

That has done the trick!

---

