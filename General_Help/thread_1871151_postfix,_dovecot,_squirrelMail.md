---
title: "postfix, dovecot, squirrelMail"
date: 2011-10-28
forum: General Help
---

### Post by pgdesign2 on 2011-10-28
Hi, I've recently set up a mailserver using postfix, dovecot which work fine, but i'm trying to get squirrelMail to use the mysql which hold the domain, users and passwords.

I've run the SM configtest.php, everything is fine but it says:

Checking database functions...
    not using database functionality.

Anyone experienced a similar issue?

Any help appreciated.

---

### Post by SeijiSensei on 2011-10-28
Perhaps you don't have the [php5-mysql]("http://packages.ubuntu.com/lucid/php5-mysql") module installed?  That provides the interface between PHP, which SquirrelMail is written in, and the MySQL server.  

In a directory that you can view with a web browser, create a file called test.php like this:

```
echo '<?php phpinfo()?>' > test.php
```

Then view that file over the network with a browser.  You'll see a list of all the installed PHP modules.  Do you have one for MySQL?

---

