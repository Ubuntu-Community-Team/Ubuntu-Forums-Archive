---
title: "urgent(Login)"
date: 2012-06-14
forum: General Help
---

### Post by musty202 on 2012-06-14
Hello,

Please i'm trying to create a simple php login page, but i keep getting this error"**Warning**: mysql_result() expects parameter 1 to be resource, boolean given  in **C:\xampp\htdocs\myticket\login.php** on line **15**
Login  Successful. Welcome Backsir/madam.", the login is working, and  displays the successful message, comes with error, below is my code
```

<?php

$username = $_POST['username'];
$password = $_POST['password'];
$login = $_GET['login'];


if($login =='yes')
{
    $con = mysql_connect("localhost","root","");
    mysql_select_db("login");
    
    $get = mysql_query("SELECT count(id) FROM login WHERE user='$username' and pass='$password'");
    
    $result = mysql_result($get, 0);
    
    if($result!=0)
    {
        echo "Invalid Login";
        
    }
    else
    {
        echo "Login Successful. Welcome Back".$_COOKIE['username']."sir/madam.";
        $_SESSION['username'] = $username;
    }
    }
?>

```

---

### Post by greenpeace on 2012-06-14
Hi,

you need to check what you're getting back from the DB.

from: [http://uk3.php.net/manual/en/function.mysql-query.php]("http://uk3.php.net/manual/en/function.mysql-query.php")
For SELECT, SHOW, DESCRIBE, EXPLAIN and other statements returning resultset, mysql_query() returns a resource on success, **or FALSE on error.**

So, are you getting an error back from your query to the DB?

consider including something like this after your call to mysql_query to help you debug it:

[PHP]if (!$get) {
    die('MySQL Error: ' . mysql_error());
}[/PHP]

Also, you really need to consider how you're building your query... you're not making safe the contents of the query... read up on SQL Injection on wikipedia.  Here's some more info:
[http://uk3.php.net/manual/en/function.mysql-real-escape-string.php]("http://uk3.php.net/manual/en/function.mysql-real-escape-string.php")

---

