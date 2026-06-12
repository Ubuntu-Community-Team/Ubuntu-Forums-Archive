---
title: "I need a foxpro replacement. any ideas?"
date: 2010-11-23
forum: General Help
---

### Post by LuniTux on 2010-11-23
Hello,

I have been using Visual Foxpro 7 under wine for about a year without any real problems. I have decided to make a vbox image of ubuntu 9.10 so that I can easily rebuild a machine in case a computer fails. The problem is that wine runs REALLY SLOW in virtualbox 3.2.8. This seems to be a know issue.

I need a programming language that can open bdfs (I can convert the file to MySQL if needed) so that specific information can be edited. The data table has about 90,000 records and needs to be able to show alot of data at one time.

I have tried Gambas2 but could not find how to access the data. I also tried qt4 but can't figure out how to write code for it or if it can access data. I can use php but it runs slower than virtual wine.

Is there any other programming language or a Gambas2/qt4 howto to access the data?

Thanks,

---

### Post by bouncingwilf on 2010-11-23
Much depends on how you need to access the data - If you need a smart GUI report generator then I'm not sure of your best way to go. I myself have a few databases containing up to a few million records each and I access the underlying [sqlite3]("http://www.sqlite.org/about.html") database(s) with a dedicated GUI app written in C/gtk+ ( the sqlite C bindings are quite straightforward) but for "ad hoc" queries, I just fire up Sqliteman and and do an SQL query.  This would of course require you to import the data into Sqlite.



Bouncingwilf

---

### Post by LuniTux on 2010-11-23
Thanks for the quick response.

The main problem is that I am trying to keep anyone from having direct access to the data file. I found the code for gambas2 but it is taking forever to load just one field. I stopped it from running at 10 minutes. I think that if I can make the program check for records that match or are close to the string searched that might be a usable solution. I would prefer to have all data shown at one time like it does in fox though.

---

### Post by blueridgedog on 2010-11-23
When I migrated away form MS Access, I went with MySQL and Perl accessed through a web browser via simple and easily cannibalized CGI scripts.  If I had to do it again, I would probably use Ruby.

---

### Post by LuniTux on 2010-11-23
It looks like I will have to go with converting the data to MySQL. I will probably go with PHP and limited search queries because the code needs to be readable by the other programmers and some of them can not read/write ruby (myself included). Ruby does look like it would be a great programming language for a more complex program so I will look into it after I finish this project. Thanks for all the help! :)

---

### Post by bompus on 2010-11-23
I also would recommend using MySQL+PHP.. You can always use phpmyadmin for some heavy duty manual work, or have a programmer make a simple interface. The good thing about PHP is that there are plenty of developers out there for it, and its fast unless someone borks it up.

---

