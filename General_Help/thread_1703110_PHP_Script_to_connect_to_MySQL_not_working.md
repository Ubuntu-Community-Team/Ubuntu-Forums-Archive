---
title: "PHP Script to connect to MySQL not working"
date: 2011-03-08
forum: General Help
---

### Post by peterv6 on 2011-03-08
I'm trying to connect to a MySQL database, PROJECT1, using a PHP script.  This works perfectly in OS X, but when I run this in Kubuntu Linux, the first echo statement executes, displaying "before link....", then nothing happens.  It should at least display the "after link...." echo statement.  
```

<?php
// CONNECTDB.PHP - Updated: Monday July 8, 2009 - 6:23 PM
echo "before link....";
//
$link = mysql_connect('127.0.0.1', 'peterv', 'password','PROJECT1');
//
echo "after link....";
if (!$link) {
   die ('Connect failed: ' . mysql_error());
   exit();
} else {
// select the database
   $db_selected = mysql_select_db('PROJECT1', $link);
   if (!$db_selected) {
      die ('Database Selection failed: PROJECT1 ' . mysql_error());
   }
}

```
If anyone can help me out with this, I'd be extremely grateful!
Peter V.

---

### Post by norima on 2013-01-28
php-mysql is not properly configured or installed

---

### Post by lisati on 2013-01-28
*Thread moved to **General Help**.*

---

### Post by lisati on 2013-01-28
Old thread closed.

---

