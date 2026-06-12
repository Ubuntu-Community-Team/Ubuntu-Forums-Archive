---
title: "PHP Sendmail using local... Windows"
date: 2011-02-08
forum: General Help
---

### Post by Jovenrp on 2011-02-08
How can I send a mail to other email using local SMTP? I need a configuration in php.ini but I cant configure it properly. Thanks... :D

---

### Post by Habitual on 2011-02-08
I am not sure why you think you need something in the php.ini

```
echo TEST| mail user@domain.com
```

and just wrap some php around that shell command.

[http://php.net/manual/en/function.mail.php](http://php.net/manual/en/function.mail.php)

---

