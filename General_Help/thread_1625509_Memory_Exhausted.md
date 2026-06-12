---
title: "Memory Exhausted"
date: 2010-11-19
forum: General Help
---

### Post by John_Needs_help on 2010-11-19
Hi,
 
I am running an Ubuntu server and I have a file called update.php in the web directory.
 
When I access the file with internet explorer on another computer on the local network, I get the following error:
 
**Fatal error**: Allowed memory size of 104857600 bytes exhausted (tried to allocate 62 bytes) in **/var/www/update.php** on line **10**
 
The code in the file is below:-
 
<?php$table = 'lookup';
mysql_connect(localhost,'cpg','Nominal1');
@mysql_select_db('cpg') or die("Unable to connect");
$colheadings = 1;
$deleterecords = "TRUNCATE TABLE '$table'";
mysql_query($deleterecords);
$pass=0;
$fail=0;
$filecontents=file("$table.csv"); [COLOR=red]# Line 10[/COLOR]
for($i=$colheadings; $i<sizeof($filecontents);$i++){$insertrecord = "Insert into '$table' Values ($filecontents[$i])";mysql_query($insertrecord);if(mysql_error()){$fail+=1;}else{$pass += 1;}}echo "Fails = $fail and passes = $pass";
?>
 
When I first ran the program the error stated that the memory of 16mb were exhausted (tried to allocate 56mb). I changed the limit at /etc/php5/apache2/php.ini from 16mb to 128mb. I now get the error above.The csv file that I am accessing is about 60mb and is located on the server.Any thoughts would be greatly appreciated.
 
Regards,
 
John.

---

### Post by Dave_L on 2010-11-19
Loading that entire .csv file into an in-memory array will take a huge amount of memory.  You could increase the memory limit further, or you change that script to process the file one line at a time.

Or you could use the MySQL query LOAD DATA INFILE:
[http://dev.mysql.com/doc/refman/5.1/en/load-data.html](http://dev.mysql.com/doc/refman/5.1/en/load-data.html)

Personally, I've found it easier to use the MySQL command line client when handling large amounts of data.

---

### Post by John_Needs_help on 2010-11-19
Dave_L,
 
Thanks for your prompt reply and sound advice.  I have used the load data infile and it is now working.
 
Regards,
 
John.

---

