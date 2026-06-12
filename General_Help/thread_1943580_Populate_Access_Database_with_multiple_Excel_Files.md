---
title: "Populate Access Database with multiple Excel Files"
date: 2012-03-19
forum: General Help
---

### Post by wewantutopia on 2012-03-19
(sorry if this is the wrong place to post this, I don't really see a better place).

I run a small flooring company.  Over the years I've created invoices using an excel template I created (I know, not the most elegant way, but it has worked).

I would now like to create a database of all my customers, addresses, phone numbers etc.

I have created a table etc etc and would like to populate the database without entering the data manually from the 100's of files.

Each invoice has the data in the same cells.  i.e.  name is b3, street b5, phone d3 etc.

Is there a way I can do this?

I am Ubuntu 9.10 with OpenOffice 3.1 and Windows XP and 7 with office 2010 (both in virtualbox) if any of these combinations will help.

Thank you!!

---

### Post by josephmills on 2012-03-19
Hello there I think that you might like this video
\\:D/
[CSV FILES TO SQL](http://www.youtube.com/watch?v=TTgdCltgkIU)
  :p

---

### Post by oldfred on 2012-03-19
I am not a python programer, but here is something to play with. I also had to add a few things like xlrd and I am not sure about all the other imports I use as I may have separately added them or they may be part of python?

I created two spread sheets with data in b3,b5,b6, & d3. I do no parsing to see if it is valid or not.

I print to terminal & to a cvs file:

```
fred@fred-LT-A105:~/Projects/parseaddress$ python parseaddress.py 
('./sheet2.xls', 'sheet2.xls', 'xls')
sheet2.xls
('sheet2.xls', u'second name', u'Second street', u'second citystatezip', u'second phone')
('./parseaddress.py', 'parseaddress.py', 'py')
('./sheet1.xls', 'sheet1.xls', 'xls')
sheet1.xls
('sheet1.xls', u'first name', u'first street', u'first citystatezip', u'first phone')

```It will not let me upload .xls or .cvs files. Screenshot of one of the .xls files and this is output:

```
sheet2.xls,second name,Second street,second citystatezip,second phone 
sheet1.xls,first name,first street,first citystatezip,first phone


```

---

### Post by Bucky Ball on 2012-03-19
From the description of this forum:

> The Community Chat area is for lighthearted and enjoyable discussions, like you might find around a water cooler at work. Almost any non-tech-support topic may be discussed here.This is not the right place either. Community Cafe NOT for support questions. I have asked mods to move to the appropriate forum. ;)

---

### Post by CharlesA on 2012-03-19
Moved to General Help.

Also note: Ubuntu 9.10 is End-of-Life and as such the choice of software may be limited.

---

### Post by wewantutopia on 2012-03-19
Thanks for all the help so far.

Sorry for posting in the wrong place, general seemed to be linux distro related only.

> **CharlesA said:**
> Also note: Ubuntu 9.10 is End-of-Life and as such the choice of software may be limited.

Yep, I know.  But it works... if it ain't broke, don't fix it.  I'll probably upgrade @ 12.04 if I can figure out a DE I like.  I really hate having to set everything up how I like it again.

---

### Post by Mark Phelps on 2012-03-20
If your questions about about using MS Access and Excel, strongly suggest you go to the Win7 forum (sevenforums.com).  

They have a section dealing specifically with MS Office and may be able to help.

---

### Post by wewantutopia on 2012-03-20
I'll check them out too.

I mostly run Ubuntu though....

If anyone knows how to do the same thing in OpenOffice that would be greatly appreciated too.

Even without the access part.  If I can combine the data from all the individual spreadsheets into one master it would be perfect.

---

### Post by oldfred on 2012-03-20
The python script I posted is for Excel, but could easily be changed to OO. It is in python3 so you may have to change to python2.

---

### Post by SeijiSensei on 2012-03-20
If you create the database in Access, you can import data from Excel directly.  The "External Data" options in the ribbon let you import from or export to Excel files directly.  Just make sure you have the field names in the first row of each Excel spreadsheet, and that at least one column is unique so it can function as a primary key.  (Access will create a primary key from 1 to N if you don't specify a key field, but you're much better off with a meaningful primary key like invoice number.)

If you want a bit of a challenge, you can use Linux to store all the data in an SQL database like PostgreSQL or MySQL, then use the appropriate ODBC connector to manipulate the data using Access or Excel.  Most of the time I use the command line and enter SQL commands directly, but for importing and exporting data, I find the Access+ODBC approach much simpler.  

The upside of putting all the data in an SQL database is that you can use a wide variety of tools to run queries including things like PHP scripts on a website.  For example, I run a little March Madness game this time of year where all my players can make their selections via a web site.  All the data are stored in PostgreSQL.  Each year I need to upload the basic information for teams like wins, losses, "RPI" and strength of schedule.  It takes me about fifteen minutes to do this nowadays.  I copy the data from the [CBS Sports website]("http://www.cbssports.com/collegebasketball/rankings/rpi/index1"), paste it to an Excel spreadsheet, import the spreadsheet to Access, then run an append query to push the data to the PostgreSQL database.  That task would have taken an hour or more without these tools.

---

