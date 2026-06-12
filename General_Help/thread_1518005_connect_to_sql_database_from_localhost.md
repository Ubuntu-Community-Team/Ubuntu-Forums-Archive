---
title: "connect to sql database from localhost?"
date: 2010-06-25
forum: General Help
---

### Post by mich4elp on 2010-06-25
Is is possible to connect to an SQL database from localhost?
I am trying to test out my website before I upload it to the server. Before, I had a problem with .php files not displaying, but instead I would be asked to download it (when it was on my hard drive) when I tried opening it with Firefox.
So, I now have all the files necessary in /var/www, or localhost, but I when I try to load the pages that need to connect to an SQL database, it does not connect. I know the username, password, and database names are fine because it works fine when I go to the website URL. However, trying to connect to them from localhost fails.
How I'm connect to the SQL databases:
```

$connection = mysql_connect('host', 'username', 'password') or die ("<p class='error'>Sorry, we were unable to connect to the database server.</p>");
$database = "database";
mysql_select_db($database, $connection) or die ("<p class='error'>Sorry, we were unable to connect to the database.</p>");
```

Is it possible that I do not have the right packages installed for MySQL? (Although I'm pretty sure I have pretty much every SQL package I would need)

---

### Post by WorMzy on 2010-06-25
How does it fail? Do you get the die message, or are you just presented with a blank page?

You have got php tags around the code, right?

It is possible to connect to a localhost database, I do it all the time.

Does [http://localhost]("http://localhost") take you to your apache server?

---

### Post by mich4elp on 2010-06-25
The page shows up until the part where the page tries to connect to the database. There is no die message.

Yes, there are PHP tags around the code.

Not exactly sure how to connect to a local database? Could you give me an example?

Going to [http://localhost/](http://localhost/) brings me to the /var/www/index.php page.

---

### Post by WorMzy on 2010-06-25
Here's an example that I use:

```
<?php
	[COLOR="Red"]$_USERNAME[/COLOR] = "*username*";
	[COLOR="Blue"]$_PASSWORD[/COLOR] = "*password*";
	[COLOR="Magenta"]$_CONNECT[/COLOR] = "*localhost*";
	[COLOR="Cyan"]$_DATABASE[/COLOR] = "*databasename*";
	[COLOR="DarkGreen"]$con[/COLOR] = mysql_connect([COLOR="Magenta"]$_CONNECT[/COLOR],[COLOR="Red"]$_USERNAME[/COLOR],[COLOR="Blue"]$_PASSWORD[/COLOR]);
	if (![COLOR="DarkGreen"]$con[/COLOR]) {
	  die('Could not connect: ' . mysql_error());
	}
	mysql_select_db([COLOR="Cyan"]$_DATABASE[/COLOR], [COLOR="DarkGreen"]$con[/COLOR]);
	[COLOR="SlateGray"]$sql[/COLOR] = mysql_query("SELECT * FROM *Tablename*");
	while([COLOR="Orange"]$row[/COLOR] = mysql_fetch_array([COLOR="SlateGray"]$sql[/COLOR])) {
	  /*CODE GOES HERE*/
	}
	mysql_close([COLOR="DarkGreen"]$con[/COLOR]);
?>

```

---

### Post by mich4elp on 2010-06-25
Sorry. The problem why I wasn't getting a message was because of permissions. Here is what I get when incorporating mysql_error():

```
Sorry, we were unable to connect to the database  server.
Lost connection to MySQL server at 'reading initial  communication packet', system error: 110
```

edit: Also, the server I am using is not hosted on my computer. I am using freehostia for my website.

---

### Post by WorMzy on 2010-06-25
I'll admit, I'm not in the least bit knowledgeable when it comes to SQL error messages; but if it's a permissions error, are you sure that you're logging into the SQL server with an account with read permissions on the database you're trying to access?

It doesn't matter that it's a remote server, the PHP runs on the server, so localhost will be treated as the server's localhost. Assuming that the server's host file has localhost defined as 127.0.0.1, of course.

---

### Post by mich4elp on 2010-06-25
I don't think that error is a permissions error, but I didn't get anything before because of permissions on Ubuntu, not on the server.
The database should be readable by localhost. I have the same files on the actual website, and it loads from the SQL database just fine.

---

