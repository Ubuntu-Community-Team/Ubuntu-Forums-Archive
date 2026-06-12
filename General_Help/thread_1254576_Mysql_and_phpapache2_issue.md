---
title: "Mysql and php/apache2 issue"
date: 2009-08-31
forum: General Help
---

### Post by paradigm2 on 2009-08-31
Hello.  I am getting:

> 
Access denied for user 'www-data'@'localhost' (using password: NO)


I know that means to check username, host, and password.  But here's the thing it is connecting to the database just fine earlier within the same page with:

```

                $username="root";
                $password="REDACTED_BY_ME";
                $database="REDACTED_BY_ME";
                        mysql_connect('localhost',$username,$password);
                        @mysql_select_db($database) or die( "Unable to select database");

```

and the code works for most of the .php file until it comes to another line of code which is executed after clicking a link.  Then it mysteriously fails.  However it is actually reading from the database just fine.

Why is it trying to connect as www-data?  Note there is a chance that I created or didn't create all the needed tables however I know the database is accessible because its the only one in the code.  If it connects and cannopt find a table would it automatically try to connect as 'www-data'?  

Just trying to figure out what is going on here.  Please help with any ideas.  If it is significant the portion where it gives this error is in a spot where it tries to write to the database....

---

### Post by paradigm2 on 2009-08-31
Here are the exact error messages

```

Warning: mysql_query() [function.mysql-query]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/front.php on line 98

Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /var/www/front.php on line 98
Access denied for user 'www-data'@'localhost' (using password: NO)

```

Running apache2 over jaunty on localhost.  The front.php file acts as a front end to a mysql database.

---

### Post by credobyte on 2009-08-31
Try it in this way .. does it really show "User: www-data" ?

[PHP]<?php

$username="root";
$password="REDACTED_BY_ME";
$database="REDACTED_BY_ME";

echo "Username: " . $username . "<br />";
echo "Password: " . $password . "<br />";
echo "Database: " . $database . "<br /><br />";

$conh = @mysql_connect("localhost",$username,$password) or die(mysql_error());
$dbh = @mysql_select_db($database) or die(mysql_error());

?>
[/PHP]

---

### Post by paradigm2 on 2009-08-31
> **credobyte said:**
> Try it in this way .. does it really show "User: www-data" ?

[PHP]<?php

$username="root";
$password="REDACTED_BY_ME";
$database="REDACTED_BY_ME";

echo "Username: " . $username . "<br />";
echo "Password: " . $password . "<br />";
echo "Database: " . $database . "<br /><br />";

$conh = @mysql_connect("localhost",$username,$password) or die(mysql_error());
$dbh = @mysql_select_db($database) or die(mysql_error());

?>
[/PHP]

Thanks will give it a try.  It is showing as 'www-data', yes.  I only made root able to access this database though.  I haven't even added 'www-data' as a mysql user.

I am a newbie to mysql and was thinking perhaps if a table didn't exist it would try to connect as 'www-data' as a last ditch effort - ever heard of that?

---

### Post by credobyte on 2009-08-31
> **paradigm2 said:**
> Thanks will give it a try.  It is showing as 'www-data', yes.  I only made root able to access this database though.  I haven't even added 'www-data' as a mysql user.

I am a newbie to mysql and was thinking perhaps if a table didn't exist it would try to connect as 'www-data' as a last ditch effort - ever heard of that?

Are you sure that it doesn't have any additional configuration files, included in front.php ( which might cause this problem due to misconfiguration ) ?

---

### Post by paradigm2 on 2009-08-31
Yes i I added those echos and initially at least it is conencted as it should:

```

Username: root
Password: REDACTED
Database: REDACTED

```

I will add the debugging info right before and after offending code line and see what it says.  Strange error...

---

### Post by paradigm2 on 2009-08-31
> **credobyte said:**
> Are you sure that it doesn't have any additional configuration files, included in front.php ( which might cause this problem due to misconfiguration ) ?


Nothing that I can see?  I am a real mysql newbie though and am pretty much just hacking around.

I put in the debug echos before the offending line and it showed as expected:

```

DEBUG: BEFORE LINE 106
Username: root
Password: XXXXXXX
Database: XXXXXXX


Warning: mysql_query() [function.mysql-query]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/front0.php on line 109

Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /var/www/front0.php on line 109
Access denied for user 'www-data'@'localhost' (using password: NO)

```

Here are the offending lines:

```

$query="SELECT mydatabase.id,url,count(votes) as count FROM mydatabase LEFT JOIN mydatabase_votes ON (mydatabase.id=url_id) WHERE hideit='No' GROUP BY (urls_id) ORDER BY url;";

$result=mysql_query($query) or die(mysql_error());

$num=mysql_numrows($result);

```

More than likely I made a mistake when I created the table structure of 'mydatabase_votes', but would that really cause such a weird error?

Note: it's called front0.php now because I saved the change version that we made so that the original copy is undisturbed.

---

### Post by paradigm2 on 2009-08-31
In looking it appears it might be related to a close() that is getting executed.  I didn't write the code but in thinking this is one of few things that would make sense.  The connection is closed so then it tries the default.  Will look more later but if anyone has possible ideas please share.

---

