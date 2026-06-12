---
title: "Mysql Ajax access denied"
date: 2011-04-14
forum: General Help
---

### Post by tunco on 2011-04-14
Hi,

There is a simple select query in a.php. If i run directly a.php, there is no problem but if i call a.php from b.html with ajax i have Access denied for user 'www-data'@'localhost' (using password: NO)error.

ubuntu 10.10
php5
mysql

---

### Post by SeijiSensei on 2011-04-14
How are you calling [mysql_connect()]("http://php.net/manual/en/function.mysql-connect.php")?  Did you give it the username (and password if needed) of the MySQL user that owns the database?

---

### Post by tunco on 2011-04-14
yes mysql user has all privileges.

$con = mysql_connect("localhost","root","1234");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

mysql_query("SET NAMES 'UTF8'");
mysql_query("SET character_set_connection = 'UTF8'");
mysql_query("SET character_set_client = 'UTF8'");
mysql_query("SET character_set_results = 'UTF8'");

mysql_select_db("depo",$con);
		
		$query=mysql_query("select * from sale_data");
		
		if(!$query){
			echo mysql_error();
		}

---

