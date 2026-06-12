---
title: "php and mysql syntax errors"
date: 2009-07-21
forum: General Help
---

### Post by benh13 on 2009-07-21
I have been learning how to use mysql and php. i am using a php tutorial website and i am trying to display data from a database. It gives this example code

```

<?php
$con = mysql_connect("localhost","peter","abc123");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

mysql_select_db("my_db", $con);

$result = mysql_query("SELECT * FROM Persons");

while($row = mysql_fetch_array($result))
  {
  echo $row['FirstName'] . " " . $row['LastName'];
  echo "<br />";
  }

mysql_close($con);
?> 

```i have edited the imformation so it corresponds with my own database and mysql. however, when i open the php file, it gives the error message
"mysql_fetch_array(): supplied argument is not a valid MySQL result resource in **/var/www/test php.php** on line **20". ** everything else is correct now to correspond with my own database, so i don't understand what i am doing wrong.can anyone help?
thanks

---

### Post by benh13 on 2009-07-21
never mind, the problem was the s in guitars

---

