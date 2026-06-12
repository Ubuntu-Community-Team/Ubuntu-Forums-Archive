---
title: "Can't connect PHP to MySQL in Kubuntu"
date: 2011-03-09
forum: General Help
---

### Post by peterv6 on 2011-03-09
I'm trying to run php scripts on Kubuntu 10.04 that connect to a MySQL database.  These scripts run perfectly on OS X 10.6.6, but when I run them in Kubuntu, I get the following error:

The script...
<?php
$mysql = mysql_connect('127.0.0.1', 'peterv', 'password');
if (mysql_connect_errno()) {
   printf("Connect failed: %s\n", mysql_connect_errno());
   exit();
} else {
   printf("Host information: %s\n", mysql_get_host_information($mysql));
}
?>

The error message:
"Fatal error: Call to undefined function mysql_connect() in..."

I've seen some posts in other boards about Red Hat problems like this, but nothing that can help with Kubuntu.  I'd really appreciate a hand with this.
Thanks,
Peter V.

---

### Post by wiggly81 on 2011-03-09
i have made a few edits and it works on my system
```
<?php
	$mysql = MySQL_Connect('localhost', 'root', 'password');
		if(!$mysql) {
			printf("Connect failed: %s\n", mysql_error());
			exit();
		} else {
			printf("Host information: %s\n", mysql_get_host_info($mysql));
		}
?>
```

hope it helps some

---

### Post by peterv6 on 2011-03-09
wiggly, thanks for the attempt, but it still doesn't work.  Since it's giving me an error for an undefined function call, I think it has something to do with my php installation.

---

### Post by wiggly81 on 2011-03-09
can you post the whole error?

---

### Post by peterv6 on 2011-03-09
Sure:

```
**[COLOR="Red"]Fatal error: Call to undefined function mysql_connect() in /var/www/LP2/dbc.php on line 2.[/COLOR]**
```

Thanks for looking!

---

### Post by norima on 2013-01-28
you installed php and mysql separately. you should install php-mysql

---

