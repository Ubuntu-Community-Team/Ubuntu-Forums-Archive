---
title: "PHP fatal error"
date: 2010-11-12
forum: General Help
---

### Post by DuXati on 2010-11-12
Hi all,

I've encountered something what seems to be a PHP bug. Whatever script I run, the result is an error stating:

```
PHP Fatal error:  Allowed memory size of 262144 bytes exhausted (tried to allocate 261900 bytes) in Unknown on line 0
Could not startup.
```

I'm not allocating a lot of memory, in fact, the PHP script is:

```
<?php
echo('test');
```

I'm using a fresh install of Ubuntu 10.10 with packages php5, php5-cli and php5-mysql. I've searched the web for this error and can't find anything useful. Does anyone have experienced this error too?

I hope it's just PEBKAC :)

Regards,

DuXati

---

### Post by linux-hack on 2010-11-12
First I think you need to close the php tag. And If you have memory problems may be this comes from the php configuration.

---

### Post by DuXati on 2010-11-12
Hi,

Thanks for the answer. I had the problem when installing some software (Drupal Aegir) using an installation script. I've now done every step of the script manually and the problem disappeared. No clue what caused it though...

Thanks for the reply.

DuXati

---

### Post by linux-hack on 2010-11-15
Can you post the script so others may use it, if you resolved your problem with it ? And put a RESOLVED in the title :D

Thanks.

---

