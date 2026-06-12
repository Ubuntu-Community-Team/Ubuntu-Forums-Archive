---
title: "How to connect PHP with Oracle-xe server when both reside on the same pc"
date: 2010-10-17
forum: General Help
---

### Post by ahmadmusaffa on 2010-10-17
Hay I ve installed oracle-xe 10g on ubuntu 10.10 32 bit. for installation i ve followed the these steps:

[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)

Now im working with my dbms. its just working fine.
for php setup i've followed this:

[http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html)

now its working great under netbeans.
The  problem is that i cannot connect php with oracle. oracle says as i've  server version installed i dont have to install client version. i  searched on the net how to set this up with no avail. instead i got  this.

[https://help.ubuntu.com/community/PHPOracle](https://help.ubuntu.com/community/PHPOracle)

it has[SIZE=1]  PHP using Oracle Database Server as TODO. so i went through the client  version installation steps but I DIDNT INSTALLED THE CLIENT. when oci8  wants to get the ORACLE_HOME location i put this  '/usr/lib/oracle/xe/app/oracle/product/10.2.0/server'
now phpinfo() shows up oci8. but when i run the code below it says not connected.

<?php     
$ora_conn = oci_connect('musaffa','oracle','localhost/XE');
if (!$ora_conn)
{ 
    echo "not connected" ;    
    oci_close($ora_conn); 
} 
else 
{
    echo "Connection Succesful\n";
    oci_close($ora_conn);
}
?>
username and password are correct.

Please help me. I want to say 'Goodbye Microsoft'.
[/SIZE]

---

