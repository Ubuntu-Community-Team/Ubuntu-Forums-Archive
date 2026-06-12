---
title: "PHP-CLI and MSSQL Connection ... ko"
date: 2012-07-24
forum: General Help
---

### Post by flyns on 2012-07-24
Hello,

this is my second thread, so I'm still new to Ubuntu and to this forum. On my first thread, I had problems connecting to a MSSQL 2008 Server, and the user Kunikili gave me the answer to my problem (thanks!), so... I'll try it again.

Now I've got my php file, with a mssql connection, and it works fine if I execute it trough a web navigator (I've tried it with Google Chrome and Explorer: ok). But I need to execute this php several times a day, so I thought I could use cron and make it work in the command line. I downloaded and installed php-cli, and started working ok... until it crashed: 

PHP Fatal error:  Call to undefined function mssql_connect() in /my/path/my_file.php on line 24

And on line 24 we find:

$connection= mssql_connect(server: port, user, port) or die ("Could not connect to SQL Server 2");

I know the sentence is ok, as it works in Google Chrome, but... it doesn't work if I use cli.

I've read in some internet forums to load the mssql.so module in php.ini, but I can't find it, and some other solutions that didn't work neither, so... can you help me?

Thanks a lot!

Flyns.

---

### Post by spjackson on 2012-07-24
A common approach is to use wget or curl from cron, so that the php code is still executed via the webserver rather than via the cli.
e.g. ```
wget -q -O /dev/null http://localhost/path/to/script.php
```

If you have a reason to use the cli instead, then
```
php --ini
``` will tell you where the system default ini file is.

---

### Post by flyns on 2012-07-25
First answer, first attempt, and problem solved! Thanks a lot, spjackson! I didn't think about this option: much faster and easier.

(Now I am only curious about why it doesn't work using php: once I know where the default ini file is... what should I do?).

Thanks,

Flyns.

---

### Post by SeijiSensei on 2012-07-25
> **flyns said:**
> (Now I am only curious about why it doesn't work using php: once I know where the default ini file is... what should I do?).

Thanks,

Flyns.

The command-line PHP executable uses a different php.ini file from the one associated with apache:

```

/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini

```

You probably need to take the same steps to activate the MSSQL module in the command-line client as you did for the apache server version.

---

### Post by flyns on 2012-08-02
> **SeijiSensei said:**
> The command-line PHP executable uses a different php.ini file from the one associated with apache:

```

/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini

```

You probably need to take the same steps to activate the MSSQL module in the command-line client as you did for the apache server version.

I'll work on it... let's see if I can handle it.

Thanks!

---

