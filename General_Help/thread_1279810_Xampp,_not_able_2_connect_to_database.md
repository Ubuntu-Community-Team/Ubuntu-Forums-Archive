---
title: "Xampp, not able 2 connect to database"
date: 2009-10-01
forum: General Help
---

### Post by Pavanrikki on 2009-10-01
Guys, i have not set username/password to my Xampp and this is the code i wrote, it's not creating a database:

<html>
<body>

<?php

$con=mysql_connect("localhost","","");
if(!$con)
{
    die("Could not connect".mysql_error());
}    
echo "connected<br />";
    if(mysql_query("CREATE DATABASE Employee",$con))
    {
        echo "Data base EMPLOYEE created";
    }
    else
    {
        echo "Could not create database " . mysql_error();
    }


?>

</body>
</html>

---

### Post by credobyte on 2009-10-01
[php]<?php
mysql_connect("localhost", "", "") or die(mysql_error());
echo "Connection established!";

mysql_query("CREATE DATABASE TestDB") or die(mysql_error());
echo "Database successfully created!";
?>
[/php]What's the output ?

---

