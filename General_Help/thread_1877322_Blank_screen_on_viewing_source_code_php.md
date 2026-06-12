---
title: "Blank screen on viewing source code php"
date: 2011-11-07
forum: General Help
---

### Post by arturo322 on 2011-11-07
**Apache2 mysql-server php5 Database error** 			
 			 			 		   		 		 		I've Installed these applications by doing

sudo su
Password: ********
apt-get update
apt-get upgrade
apt-get install apache2 mysql-server mysql-client php5


after installation

i tried typing localhost on my browser it printed
IT WORKS!

so assuming everything was right i copied my sourced codes on /var/www/Mysourcecodes
when i opened it by typing /localhost/Mysourcecodes it gives me a blank  screen. i searched the internet for possible errors it's said that its a  mysql error on php so i removed my sourcecode for connecting to the  database server and retyped localhost/Mysourcecodes and yeah my expected  page popped out BUT it cannot connect to the database since i removed  my sourcecode



here is the source code i made

Conn.php
<?php 
 
$HOST = "localhost"; 
$USER = "root"; 
$DBUSERPASS = "pass"; 
$DBNAME= "dbname"; 
 
$connect= mysql_connect($HOST,$USER,$DBUSERPASS); 
 
if(isset($connect)){ 
    $dbselect = mysql_select_db($DBNAME,$connect); 
    if(isset($dbselect)){} 
    else echo "Invalid Database Name"; 
}else echo "Cannot Connect to Database"; 
?>



Heres how i called the connection file.

sample.php
<?php 
include("db/conn.php"); 
session_start(); 
?>

---

### Post by lisati on 2011-11-07
A couple of questions:
[LIST=1]
[*]Is /var/www/Mysourcecodes a directory or a file?
[*]If /var/www/Mysourcecodes is a directory, do you have a file index.php?
[*]Does the index.php file contain something similar to your "sample.php" code or does it include code to output some html?
[*]Do you have a /var/www/Mysourcecodes/db directory which includes the file conn.php?
[/LIST]

---

### Post by arturo322 on 2011-11-07
couple of questions:

Is /var/www/Mysourcecodes a directory or a file?        
Its a directory/folder

If /var/www/Mysourcecodes is a directory, do you have a file index.php?
Yes

Does the index.php file contain something similar to your "sample.php" code or does it include code to output some html?
Yes

Do you have a /var/www/Mysourcecodes/db directory which includes the file conn.php?
Yes


Actually I've had this working on Xampp/Lampp before but when i tried migrating my source codes on php5 mysql-server and apache2 I've got this problem

---

