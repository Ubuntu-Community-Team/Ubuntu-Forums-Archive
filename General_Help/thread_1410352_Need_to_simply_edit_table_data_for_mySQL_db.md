---
title: "Need to simply edit table data for mySQL db"
date: 2010-02-18
forum: General Help
---

### Post by c_martini on 2010-02-18
I have tried a few packages but cannot find an easy intuitive interface for editing tables in a mySQL database. I just need to simply edit the table field data, import and export multiple rows, and filter the table data so only the rows are returned based on a string that I search for. The tables I edit have several thousand rows and some up to 30,000. I do not know how to write queries and it seems all these packages require that you know how to write sql queries to do what I need to do. On the mac I used Sequel Pro, which is dead easy to use and is mostly point and click to do all the above. Since my mySQL experience is very limited, I really need something simple like this.

I have tried:

MySQL Workbench
Navicat (lite version)
MySQL Query Browser

I can't easily figure out how to do what I need to do with the above packages.


Any suggestions?

:confused:

---

### Post by DaithiF on 2010-02-18
you could try phpmyadmin
it allows you to browse & search in tables, and having created a search/filter graphically it then shows you the sql query it generates (as well as the results of course). So in case you are interested in understanding SQL it could be a learning tool for you.

---

### Post by c_martini on 2010-02-18
> **DaithiF said:**
> you could try phpmyadmin
it allows you to browse & search in tables, and having created a search/filter graphically it then shows you the sql query it generates (as well as the results of course). So in case you are interested in understanding SQL it could be a learning tool for you.

Yeah I wanted to try this but the head developer that is administrating our development servers will not allow us to run php on them. Is there any way I can install this locally on my machine without having to rely on php running on a server?

I guess I could try setting up a server on my local machine but it seems overkill for what I need to do...

---

### Post by DaithiF on 2010-02-18
> **c_martini said:**
> Yeah I wanted to try this but the head developer that is administrating our development servers will not allow us to run php on them. Is there any way I can install this locally on my machine without having to rely on php running on a server?

I guess I could try setting up a server on my local machine but it seems overkill for what I need to do...
you need a php-enabled web server, so if the development server is not an option then it would have to be on your local machine.  You can run phpmyadmin on your machine and have it connect to the database on the development server.  Installation isn't hard -- there are plenty of forum posts that have covered LAMP stack & phpmyadmin installs.

---

### Post by Maheriano on 2010-02-18
Another suggestion for PHPMyAdmin.

---

### Post by oldfred on 2010-02-18
Have you tried Kexi. It is Kubuntu, so it will install a few libraries but seems to work. For some dB's you have to add extra drivers to access them.

---

### Post by c_martini on 2010-02-25
> **oldfred said:**
> Have you tried Kexi. It is Kubuntu, so it will install a few libraries but seems to work. For some dB's you have to add extra drivers to access them.

I am trying this now but it only seems to want to import databases or create new database projects. Maybe I am not understanding this correctly, but this does not seem to be what I am after. I simply need to edit the data in tables on an existing remote database. I did this so easily with Sequel Pro on the mac, but thus far have not found anything that even comes close on Linux or Windows :confused:

---

### Post by oldfred on 2010-02-25
I do not have mySQL so I have not tried anything with it. Kexi it turns out in reading the fine print does use mySQL but only with db's it has set up.

Another to experiment with is knoda. It lists mySQL, I have used it to connect to my sqlite3 db. The query design view is a little more like access in that you click on a table and then on fields in that table.

---

