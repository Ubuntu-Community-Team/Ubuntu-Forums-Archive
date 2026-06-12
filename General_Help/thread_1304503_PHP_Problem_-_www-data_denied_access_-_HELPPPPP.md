---
title: "PHP Problem - www-data denied access - HELPPPPP"
date: 2009-10-29
forum: General Help
---

### Post by Rapster on 2009-10-29
Hi and hello to everyone!

I have been a Windows man all my adult life. I'm also a developer, but I've only developed in Windows based technologies (.net using Visual Studio on the whole).

However, I recently decided to try out non-Windows technologies. I have always been a bit wary of them (probably because of ignorance!), but I said 'What the heck: if you can't beat them, join them!'.

So, I completey reinstalled my laptop with Ubuntu (Jaunty whats-its-name! - 9.04). That was fairly painless. I downloaded a concise Ubuntu guide, and read through it in a day, and on the whole, I'm really impressed with Ubuntu (and therefore Linux in general). Great start.

Then yesterday, I decided to install Apache/PHP/MySQL (I used the command sudo tasksel install lamp-server), so that I could start learning PHP/MySQL. Believe me, I really want to run headlong into non-windows based technologies. Anyway, all seemed well - I wrote my first PHP script, named it index.php, and put it in /var/www/. Opened up the browser, navigated to localhost, and there it was - my first foray into non-Windows based stuff... and I liked the feeling!

Then I created a new DB in MySQL, created a table, added data to it, and then wrote a stored procedure, that would be used by the php script to retieve the data. I modified the code in my index.php, saved it, refreshed the page, and guess what? A problem! 

Access denied for user 'www'@'localhost'(using password: no) in /var/www/index.php on line 12.

So, right away, i started trawling through loads of forums. I tried different things (I even installed PHPmyadmin, but couldn't find how to access that!!!), but in the end I'm still where I was... with the problem. 

One problem might be that I still don't really understand the whole Linux way of doing things, but whatever, it's utterly pissed me off, and if I can't get this sorted out, well I hate to say it bit it could be the end of my non-Windows based days - which i certainnly hope doesn't happen.

So, please, someone.... help me!

many, many thanks in advance...

Cheers,
Tony

---

### Post by jasonlfunk on 2009-10-29
Access denied for user 'www'@'localhost'(using password: no) in /var/www/index.php on line 12.

This is telling you that on line 12 of index.php, you tried to log into mysql using the username www with no password. You will need to change index.php to use the right credentinals to login to mysql.

---

### Post by Rapster on 2009-10-29
Hi!
 
Thanks for the reply.
 
Firstly, my script isn't using www-data to connect to the database. I started using root as the user to connect to MySQL, but got the same message. Then, I created a user, and still the same error... this really frustrating!
 
Cheers,
Tony

---

### Post by Rapster on 2009-10-29
...and here's the entire code for the index.php script:

<?php
ini_set("display_errors", 1);

$mysqli = new mysqli("localhost", "root", "mysql1234", "TonyTestDB");
if (mysqli_connect_errno())
die ("Error connecting MySQL: ".mysqli_connect_error());

$sql1 = "call GetUsers()"; //GetUsers is a stored proc in MySQL

$query1 = $mysqli->query($sql1);

$rt = mysql_query($query); 

echo "$rt[FName], $rt[SName], $rt[UName], $rt[PWord]<br />";

?>

Cheers,
Tony

---

### Post by Rapster on 2009-11-03
Hi all!
 
I found out (via another forum) that my script was mixing up ordinary mysql and mysqli functions. So, the answer wasn't anything to do with permissions at all, despite the confusing error message!
 
I hope this might be useful for amyone else.
 
Cheers,
Tony

---

