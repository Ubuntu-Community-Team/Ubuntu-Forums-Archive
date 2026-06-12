---
title: "Database browser/viewer for Progress database?"
date: 2012-01-10
forum: General Help
---

### Post by Devilman13 on 2012-01-10
I've recently come across some files on our SCO system with the extensions .db and .db1. I understand that "db1" files are only (or mainly) used by "Progress" database. [http://www.progress.com/en/index.html]("http://www.progress.com/en/index.html")

The smaller database files will load in Gedit. I see clearly see data that makes sense to me in there, though it is wrapped in a lot of \00\00\00\00\00\00\00\00\00\00 and the larger files cause Gedit to hang.

SQLite browser won't open them.

Can anyone recommend a way for me to view these files correctly in Ubuntu? Perhaps I'm missing some libs or something?

---

### Post by SeijiSensei on 2012-01-10
Do you have a valid Progress license file installed?

I don't know about Ubuntu, but you can try installing an [ODBC driver]("http://www.datadirect.com/index.html") in Windows and look at the data with Access or Excel.  

I did a quick Google search to see if there is a native Linux client but wasn't successful.  Perhaps Progress can help?  If you have a license, you've paid for support.

---

### Post by Devilman13 on 2012-01-10
> **SeijiSensei said:**
> Do you have a valid Progress license file installed?

I assume that the guys that setup the SCO Openserver 6 must have (SCO in itself is license HELL from what I understand). I will probably contact one of those dudes tomorrow to at least confirm that these ARE Progress database files that I'm trying to extract data from. My ultimate goal with this would be to have some web scripts interact with the information stored in these databases, though I assume I'll probably have to port the stuff to MySQL or something first to get that accomplished. 

> **SeijiSensei said:**
> I don't know about Ubuntu, but you can try installing an [ODBC driver]("http://www.datadirect.com/index.html") in Windows and look at the data with Access or Excel.  


Yeah, I'm still relatively new to understanding all of this. I wondered about the ODBC libs I saw in package manager. The database program in Libre Office displayed the database much like the text editor. It would appear that nothing I have currently on my Ubuntu machine understand some sort of characters or something within the Progress DB. 

Anyway, thanks for your input on this Sensei. I figured this is am obscure subject that I'll mainly end up sorting by myself and the guys that know the SCO sys better, but wanted to throw it out here and see what people said.

---

### Post by SeijiSensei on 2012-01-11
> **Devilman13 said:**
> My ultimate goal with this would be to have some web scripts interact with the information stored in these databases, though I assume I'll probably have to port the stuff to MySQL or something first to get that accomplished.

You can communicate with ODBC-compliant databases in [PHP]("http://www.php.net/manual/en/book.uodbc.php").  I don't see a native Progress interface for PHP, though.

---

### Post by mbuell on 2012-01-11
> **Devilman13 said:**
> I assume that the guys that setup the SCO Openserver 6 must have (SCO in itself is license HELL from what I understand). I will probably contact one of those dudes tomorrow to at least confirm that these ARE Progress database files that I'm trying to extract data from. My ultimate goal with this would be to have some web scripts interact with the information stored in these databases, though I assume I'll probably have to port the stuff to MySQL or something first to get that accomplished. 

I think that would be my first step - see if you can confirm what database program originated the files, and work from there. Looking at these file extensions will NOT tell what they probably are. There are probably thousands of apps using ".db", and I'll guess that assuming an association between ".db1" and Progress is a very long shot. 

I don't have a clue how good the LibreOffice (OpenOffice) import stuff is, but I agree with giving it a shot from Access if you have that available. This is not a function I have compared between OO and MS Office - but in other ways I have found OO to be about 10% behind MS Office in functionality. 

Prior reply that mentioned ODBC compliant is also a good thought, but I would think if they were ODBC compliant, the OO database would open them. 

It would be nice to learn what you find out.

---

### Post by mbuell on 2012-01-11
One other note: should you feel you NEED to recover the data in these, and all else fails - almost 20 years ago I used a raw disk editor to do such a thing. It allowed direct access to the data. I cut out all the program added crap (proprietary), then saved the files. Re-opened them in something else and spent some time washing, cleaning, and tidying up. 

Tedious, doable, with large amounts of data it could be monstrous. If I recall correctly, such an editor is also called a hex editor. I'm sure somebody here will know exactly what I mean and pop up with "oh, yeah! You mean xyz!" But it was a while back for me.

---

### Post by SeijiSensei on 2012-01-11
> **mbuell said:**
> Prior reply that mentioned ODBC compliant is also a good thought, but I would think if they were ODBC compliant, the OO database would open them.

It would require a Progress-specific ODBC driver to be installed that OO could use.  From what little I know of Progress, if there is such a driver, you'd need to purchase it separately.  

There are [ODBC implementations for Unix]("http://www.unixodbc.org/") though I haven't tried them.  I use PostgreSQL pretty much exclusively, and the (free, naturally) Windows ODBC driver for Postgres works like a charm with applications like Access.

I don't see Progress in this [list of unixODBC drivers]("http://www.unixodbc.org/drivers.html").

---

### Post by Devilman13 on 2012-01-13
Alright. I got some answers today after talking to the programmer dude that set up the SCO and all. It's disappointing, but not entirely surprising.

The .db and .d1 files located on the SCO server that are used for our accounting program are not even database files! The accounting program was written in some version of BASIC (Compiled with Basmark) and those d-files are nothing more than stored data. An include file describes what layout to read/write in a record. 

He said himself he's tried to think of ways to clean up this stuff into a more readable format but he "couldn't even grab all of it if he managed to figure out a way.".

Thanks again for everyones input.

---

### Post by SeijiSensei on 2012-01-13
> **Devilman13 said:**
> The accounting program was written in some version of BASIC (Compiled with Basmark) and those d-files are nothing more than stored data. An include file describes what layout to read/write in a record.

I haven't programmed in BASIC in decades, but if you know the data file formats, couldn't someone write a simple translation program that reads the data in and writes it back out as comma- or tab-delimited files?  It doesn't sound like the data have a relational structure, so just exporting the tables should be sufficient.  Pretty much any spreadsheet or database program can import those formats.

---

### Post by Devilman13 on 2012-01-13
He's actually doing that very thing with some tasks. He's exporting some data from invoices to comma delimitted text and then injecting that into a java program to produce spread sheets. It looks like I'll have to try to take a stab at doing the same... though no clue this point if I can. Like you, I haven't used BASIC in many, many years for anything.

---

