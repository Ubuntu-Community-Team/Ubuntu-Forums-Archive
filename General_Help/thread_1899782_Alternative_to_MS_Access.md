---
title: "Alternative to MS Access?"
date: 2011-12-24
forum: General Help
---

### Post by NautiusMaximus on 2011-12-24
Now I know this question has been asked on these forums many times before, but it looks like it hasn't been asked all that recently, and things change, so I thought it's worth another go.

I'm doing pretty well at ditching Windows and using Ubuntu for all my home computing needs, but the one thing for which I still need to use Windows is if I want to use an Access database.

Now, I know that there are some fantastic database backends like MySQL or PostgreSQL that I can use with Ubuntu, but I've not seen any database front end to rival Access for usability. LibreOffice Base does the job, I guess, but it seems awfully clunky in comparison.

Does anyone have any suggestions for anything else to look at? I don't mind getting my hands dirty with a bit of programming if need be, but would prefer to avoid doing too much if possible.

Thanks
NM

---

### Post by Lars Noodén on 2011-12-24
Take a look at [Kexi](http://www.kexi-project.org/).  It is very easy to use if you are coming from a MS Access legacy.  I've seen people whip up databases in minutes with it.   It's part of KDE but you can install it on any Ubuntu variant.

---

### Post by 73ckn797 on 2011-12-24
I would also like a simple database program. Libre Office is very involved, to me, too much like MS Access.

Back in the early 90's when I bought my first 286 computer, it came with GeoWorks, which became ArkosWorks, Ensemble which had a flat file (I believe that was what it was) database. It was quite simple to setup fields and organize a form layout. I used it for a number of years in my business but GeoWorks/ArkosWorks went away. I tried using Access but it was just too steep of a learning curve for my desires. I guess that by now I could have learned it but ended up creating a spreadsheet that I have used for over 10 years.

Do you know of a simple database that could be a simple setup? I see the Keri recommendation but would rather not have all of the KDE stuff.

---

### Post by oldfred on 2011-12-24
I have been playing with python and either gtk with glade or qt with qt designer, but find that pretty complex. Some things you can do pretty quick, but once you want more than just a query & table it is difficult.

I did find these but have not tried them.

Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/)

---

### Post by 73ckn797 on 2011-12-24
> **oldfred said:**
> I have been playing with python and either gtk with glade or qt with qt designer, but find that pretty complex. Some things you can do pretty quick, but once you want more than just a query & table it is difficult.

I did find these but have not tried them.

Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/)

My database use would be not for tracking collections or books and CD's. I enter info dealing with daily work assignments, the client, claim numbers, mileage driven for each assignment with cumulative totals, location names and city, # of photos taken on each assignment with cumulative totals, payment info for each. I currently have a spreadsheet that has 7 pages. A front page with YTD totals (for year end tax summary) individual quarterly pages, Mileage summary page and pay info page. All are interlinked so that the info in the quarterly pages, and pay page is shown in the summary pages. The old database I referred to was also able to do this but I did not have to specify relational aspects, which was the nightmare of OO/Libre Base and Access. Also form creation was much easier.

I probably have the best setup and should not consider changing. The only other feature I would like would be the ability to link the stored photos Zip files to each individual assignment entered. That would make for a simple click deal to bring up the zip file in Evince.

---

### Post by NautiusMaximus on 2011-12-26
Thanks for the suggestion for Kexi. I did have a look, but I notice that the reviews in the Ubuntu software centre say that it's rather buggy. I installed it and tried to import an Access database (which it claims to be able to do), but sadly didn't even get as far as being able to find one. Its import wizard opened a file browser that didn't actually work. So I'm inclined to believe the reports that it's buggy.

I wonder if the way to go might be to create web pages as the front end using something like PHP, Python, or another scripting language? Would something like [PostgreSQL PHP Generator]("http://www.sqlmaestro.com/products/postgresql/phpgenerator/") be helpful? (Probably not that exact thing, because it doesn't look like it's available for Linux, but I guess there must be others out there like it.)

Is that a viable route? I'm not familiar with any of those languages, but I am pretty familiar with SQL syntax, and I guess it wouldn't kill me to learn a new scripting language. And if so, are some languages better than others for this sort of thing?

Or is that vastly over-complicating things?

---

### Post by Lars Noodén on 2011-12-26
You can use LibreOffice Base for a front-end to MySQL or maybe Postgresql.  LibreOffice supports scripting with Javascript and Python.

AFAIK there's nothing that can actually read data from a legacy app like MS Access.  I'm not sure how to get the data in, but Kexi is easy to use aside from that.

---

### Post by oldfred on 2011-12-26
I was able to convert a Access 2000 db. But it only converts data & I think I got the queries. I also think it showed the names of forms & reports but does no conversion.

In the repository is mdbtools, libmdbtools, and mdbtools-gmdb that allows conversion and export.

I think most of the openoffice tools only work in Windows as it relies on the dll from Access.
[http://dba.openoffice.org/drivers/mdb/index.html](http://dba.openoffice.org/drivers/mdb/index.html)
[http://sourceforge.net/projects/mdbtools](http://sourceforge.net/projects/mdbtools)


Convert from MSAccess to sqlite using Jackcess
[http://code.google.com/p/mdb-sqlite/](http://code.google.com/p/mdb-sqlite/)
Java MSAccess tool
[http://jackcess.sourceforge.net/](http://jackcess.sourceforge.net/)

---

### Post by NautiusMaximus on 2011-12-27
I'm not hugely concerned about being able to convert my data. There are many ways of doing this, so if one doesn't work, I'm confident that another will. If it turns out to be a bit of a pain, that's fine, because I only have to do it once.

The reason why being unable to convert an Access database in Kexi puts me off is not that I think I won't be able to get at my data, but just because it seems to confirms the reviews of the software that it's buggy to the point of being unusable.

I may have another little play with Kexi to see if I can get it to do something else without falling over, but the more I think about this the more I think some kind of web-based front end might be the way to go. I suspect it's going to be a bit more of a pain to set things up, but once I have things working then it's a very robust and future proof system, right? Also unlikely to face limitations in functionality (as I believe Kexi does), given that I should be able to execute any SQL that I wish and use whichever scripting language I go for to do anything more complicated than what can be done with straight SQL.

Does that sound reasonable, or am I underestimating the complexity of doing things this way?

---

### Post by NautiusMaximus on 2012-01-21
Well, I had another play with Kexi, and although it looks like it should be a nice little program in theory, in practice it was so buggy as to be unusable.

I gather it has a KDE heritage, so maybe folks using Kubuntu would have better luck with it.

Anyway, I have now managed to put a couple of my databases onto a PostgreSQL back end, and have been working on a web-based front end using PHP. It's a little bit more programming effort than I would ideally have liked, but PHP seems like a very easy language to learn, and it also means that it's very flexible and I can do pretty much anything I want. A further advantage is that I can interact with my databases not only from my PC, but also from my phone or my Android tablet.

So despite the extra effort involved in getting it set up, I think the advantages of doing things that way make it a good solution. If anyone else is wondering how to ditch MS Access, I can highly recommend spending a bit of timing learning some PHP.

---

### Post by Lars Noodén on 2012-01-21
Good that you've found PHP easy to use.  I used to use it with MySQL a long time ago.  Two tips: 

If you're not doing this already, use [prepare](http://php.net/manual/en/function.pg-prepare.php) and [execute](http://www.php.net/manual/en/function.pg-execute.php) statements with placeholders.  

And always clean and validate incoming data.  If PHP has a [taint mode](https://wiki.php.net/rfc/taint) like perl does to track variables, then by all means remember to use it.

Have fun.

---

### Post by NautiusMaximus on 2012-01-21
Thanks for those tips, Lars, I'm sure that's going to be useful!

---

