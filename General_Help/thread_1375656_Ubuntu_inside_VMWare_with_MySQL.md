---
title: "Ubuntu inside VMWare with MySQL"
date: 2010-01-08
forum: General Help
---

### Post by ProfessorSr on 2010-01-08
I am running a vmware virtual machine with Ubuntu as the OS. I have installed MySQL with gui. The computer running this setup is in Kentuxky and I am in Arizona.
 
Using a desktop sharing program, I setup the above. If I run the MySQL Administrator from here in AZ and enter the ip address I get a connection to the db in KY and I have all of the priveledges that I set up for that account. Now, when I go to a page that accesses the db to display information from db, I get a blank page, and when I view the source all I get is:
 
```
 <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<HTML><HEAD>
<META content="text/html; charset=windows-1252" http-equiv=Content-Type></HEAD>
<BODY></BODY></HTML>

```
[COLOR=#0000ff][/COLOR] 
Below is my connection string. 
 
```
<?php
# FileName="Connection_php_mysql.htm"
# Type="MYSQL"
# HTTP="true"
$hostname_mytherapysession = "173.162.21.226";
$database_mytherapysession = "mytherapysession";
$username_mytherapysession = "********";
$password_mytherapysession = "********";
$mytherapysession = mysql_pconnect($hostname_mytherapysession, $username_mytherapysession, $password_mytherapysession) or trigger_error(mysql_error(),E_USER_ERROR); 
?>
```
 
 
[COLOR=#0000ff][/COLOR] 
I am totally lost and need any assistance anyone is willing to give me. Thank you iun advance.

---

