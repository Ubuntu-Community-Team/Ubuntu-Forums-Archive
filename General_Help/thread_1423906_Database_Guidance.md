---
title: "Database Guidance"
date: 2010-03-07
forum: General Help
---

### Post by NertSkull on 2010-03-07
So I've been using ubuntu for a while now and one of the only few things that keeps me tied to windows still is databasing.  I know linux has great utilities for databasing, I just have a bunch of databases in MS Access that are rather important and I can't just quit on.

But I've decided I want to start figuring out how to move over everything to linux.  Here are my questions/needs.

What should I use to do this?

I figure my options are SQLite, MySQL or OpenOffice Base (p.s. I'm new at linux database stuff, so I may be totally confused or making stuff up thats wrong, this is my understanding thus far).

I don't need web access, but I'm not sure I want to rule that out for the future, although its highly unlikely.  I just need to be able to use the databases locally.

I do need multiple users on my machine to access the database.  I guess they don't really need different accounts for the database, but many people log into this machine and ideally they all should have access to it.

I feel that I'm leaning towards OO Base because it has a feel similar to Access which I'm already comfortable with.  Is this a bad idea?  Will Base likely be a stable and long-term solution?

From my understanding, MySQL could also be good.  But then I'd have to set up Apache, PHP and such things.  Is that true?  I don't have a great desire to do all that, but I could. 

So if I use MySQL my understanding is my database would be "online" through a localhost webserver (I don't want it accessible from the outside,....yet).  If thats right, it seems if I go with MySQL I'm going to have to do a lot of PHP and HTML coding as well.  Am I confused?

Allright I think thats good for now.  I've been reading all morning but everything about MySQL I find is for hosting websites.  I'm not finding exactly how to use it simply as a local database for things like cataloging or finances or similar.

Thanks everyone

p.s. If I do use Base.  Is there a way to migrate my MS Access database into Base??

---

### Post by matthewboh on 2010-03-07
> I feel that I'm leaning towards OO Base because it has a feel similar to Access which I'm already comfortable with. Is this a bad idea? Will Base likely be a stable and long-term solution?


OpenOffice will be around for quite awhile.  Enough people now use it that it will have it's own life even if Sun drops it.

> From my understanding, MySQL could also be good. But then I'd have to set up Apache, PHP and such things. Is that true? I don't have a great desire to do all that, but I could.

No, you don't need to set up all the rest.  MySQL can stand on it's own.  It's more like talking about Microsoft SQLServer - so Access = Base and MySQL = MS SQLServer.  

> So if I use MySQL my understanding is my database would be "online" through a localhost webserver (I don't want it accessible from the outside,....yet). If thats right, it seems if I go with MySQL I'm going to have to do a lot of PHP and HTML coding as well. Am I confused?

Yes, you are confused.  You can connect to MySQL databases using Base and ODBC without having to use Apache or PHP.  

> Allright I think thats good for now. I've been reading all morning but everything about MySQL I find is for hosting websites. I'm not finding exactly how to use it simply as a local database for things like cataloging or finances or similar.

You can do a lot with MySQL - and it might be a good backend for your data.

Basically, you have to be a bit careful when creating your Base application.  You have to separate out the forms, etc from your database - almost the same way that Microsoft suggests setting up a multiuser application.

You can, of course, just use Base as the front end to MySQL - which might be a better situation for you.  That way, you can really scale it / change it / do web front ends.

> p.s. If I do use Base. Is there a way to migrate my MS Access database into Base?? 

There's a couple of ways to do this.  You can read Access databases in Base, so you could just do a transfer through that methodology.  You can also get one of the ETL tools that are available such as Talend - but that would require a bit of a learning curve.

There is also MySQL Workbench which has a wizard to convert Access databases to MySQL in case you decide to move to MySQL.

---

### Post by oldfred on 2010-03-07
I would look at these also.

I believe you have to create and use external databases from kexi, you cannot link to one you create outside of kexi:
[http://www.kexi-project.org/](http://www.kexi-project.org/)

KDE but works in Gnome
[http://knoda.sourceforge.net/](http://knoda.sourceforge.net/)

python front end 
[http://dabodev.com/news](http://dabodev.com/news)

I found several ways to convert msaccess. Kexi works with add ins.
In the repository is mdbtools, libmdbtools, and mdbtools-gmdb that allows conversion and export.

I have not found anything that is totally like Access. I always set up Access as a frontend/backend and if more than 3 or 4 users moved the backend to SQL server with ODBC connections. You can start by moving the Access data in the back end to any SQL server that has an ODBC connection. But you have to rebuild queries, forms & reports for any other system.

---

