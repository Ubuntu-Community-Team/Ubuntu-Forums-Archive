---
title: "Installed PostgreSQL, command postgres not found"
date: 2006-02-28
forum: General Help
---

### Post by Garyu on 2006-02-28
Hey,

I followed this howto to get PostgreSQL to work:
[http://oakley.bioinformaticsonline.co.uk/archives/2005/11/09/postgresql-on-ubuntu-linux-how-to/](http://oakley.bioinformaticsonline.co.uk/archives/2005/11/09/postgresql-on-ubuntu-linux-how-to/)

...but the command "postgres" can not be found. I would usually just type "post" and press TAB once or twice, but no commands beginning with "post" are present in the system it seems. I tried searching for files, but I only find settings. "ls -lR | grep postgres" came up with some results, but it doesn't show which folder the files are in... :(

---

### Post by Sendervictorius on 2006-02-28
There is no command in postgresql that starts post..., so that won't work.

The link you gave showed an example of changing users with "sudo su" to a user named "postgres" - the default user for the database. Then he creates a new database called mydb.

If you want the postgresql command-line interpreter you type "psql <database name>".
to create a database the command is "createdb <database name>"
to add a user the comand is "createuser <username>"
Then to do stuff in the database, you start up psql, and...

I think the sudo su may have confused you.

Perhaps some more reading about postgresql would be in order? There is heaps around. Just do a google search on "postgresql howto ubuntu" etc

Hope that helps.

---

### Post by Garyu on 2006-02-28
duh... wow, am I stupid sometimes or what...

I read the howto and was like "why not just use sudo su once, and then type in the commands". *sigh* Always read the manual... Oh well, thanks for your reply, it works like a charm when I actually do what I was told. :P

---

### Post by p0pnfresh on 2006-08-28
Oh, nice. If psql runs does it mean the postgresql server is running? My postgresql works fine, I did what was explained above, and can edit the dabase with psql. However, Glom doesn't connect to the postgresql server, which is set as localhost.

---

