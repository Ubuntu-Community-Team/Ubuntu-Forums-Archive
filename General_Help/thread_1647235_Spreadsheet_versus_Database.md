---
title: "Spreadsheet versus Database"
date: 2010-12-17
forum: General Help
---

### Post by astrobob.tk on 2010-12-17
Hello guys,

I am trying to create several databases of my books, ebooks, music, cd & dvd collection, records, & other stuff.

I was wondering what is the difference between a spreadsheet & a database (as in OpenOffice.org Spreadsheet & Base) & what each is better for ?

What do you prefer ? & why ?

Your replies are greatly appreciated.

---

### Post by bouncingwilf on 2010-12-17
I'm sure someone will come along and correct me but essentially, spreadsheets were based on a need to deal with "accountancy" type problems where there were lots of columns of info, some of which were products/sums of other columns/cell.

Databases were designed to store data and subsequently access same data in a variety of ways.

It used to be the bane of my life trying to stop people using spreadsheets to store data. Eventually the data gets too much or too complicated and it all ends in tears.   Basically, my opinion is that if you want to store data, use a database. There are plenty of good free ones out there to choose from.


Bouncingwilf.

---

### Post by BlueSpecial on 2010-12-17
> **bouncingwilf said:**
> I'm sure someone will come along and correct me but essentially, spreadsheets were based on a need to deal with "accountancy" type problems where there were lots of columns of info, some of which were products/sums of other columns/cell.

Databases were designed to store data and subsequently access same data in a variety of ways.

It used to be the bane of my life trying to stop people using spreadsheets to store data. Eventually the data gets too much or too complicated and it all ends in tears.   Basically, my opinion is that if you want to store data, use a database. There are plenty of good free ones out there to choose from.


Bouncingwilf.

Agree 100%. If you need a database use a database software. Databases are relational so they have less redundancy. Here's an example:

On Excel you have names and cities like this:

John - London
Mary - London
Brad - Liverpool
Patrick - Bristol
Sue - Liverpool

As you can see you have London and Liverpool written twice! This is called **database redundancy**. And if instead of Liverpool you made a mistake and wrote *Liverpoll* you can imagine all the errors that this would mean. Imagine this not in 5 rows but in a million of rows.

On the other hand, on a database you have typically this:

A *Cities *table like this:

**_CityID - CityName_**
1      - London
2      - Liverpool
3      - Bristol


and a *Persons *table:

**_PersonName - City_**
John        - 1
Mary        - 1
Brad        - 2
Patrick     - 3
Sue         - 2

As you can see you only have London written ONCE on the database but you can relate it with other tables... less redundancy, less errors.

On Excel if you have written Liverpool badly you have to correct it ON ALL RECORDS. On a database you just go to the Cities table, correct the name ONCE and as the other tables relate to it by is ID the changes would reflect on ALL DATABASE RECORDS.

So database WITHOUT A DOUBT!

---

### Post by astrobob.tk on 2010-12-18
> **BlueSpecial said:**
> Agree 100%. If you need a database use a database software. Databases are relational so they have less redundancy. Here's an example:

On Excel you have names and cities like this:

John - London
Mary - London
Brad - Liverpool
Patrick - Bristol
Sue - Liverpool

As you can see you have London and Liverpool written twice! This is called **database redundancy**. And if instead of Liverpool you made a mistake and wrote *Liverpoll* you can imagine all the errors that this would mean. Imagine this not in 5 rows but in a million of rows.

On the other hand, on a database you have typically this:

A *Cities *table like this:

**_CityID - CityName_**
1      - London
2      - Liverpool
3      - Bristol


and a *Persons *table:

**_PersonName - City_**
John        - 1
Mary        - 1
Brad        - 2
Patrick     - 3
Sue         - 2

As you can see you only have London written ONCE on the database but you can relate it with other tables... less redundancy, less errors.

On Excel if you have written Liverpool badly you have to correct it ON ALL RECORDS. On a database you just go to the Cities table, correct the name ONCE and as the other tables relate to it by is ID the changes would reflect on ALL DATABASE RECORDS.

So database WITHOUT A DOUBT!


thx [bouncingwilf]("http://ubuntuforums.org/member.php?u=1074036") & BlueSpecial; but how exactly would that help regarding building a library database, software database, astronomical observations database or the like ?
In the case of books & software, it might be clear to you already; but regarding tehe observations what I need to do is a database for my records with fields like:

star name
magnitude (mag)
comparison mag 1
comparison mag 2
ID (this should be an automated id number for the record which is flexible to when the records are sorted by data)
notes

To  get an idea of what else, i attached a .odb (OOo Base) [apparently i cant uplad a .db file; so here it is on [rapidshare]("http://rapidshare.com/files/438017005/VSO_Records.odb")] file which I created lately. I never used a database software, but surely I did loads of spreadsheets; so I find the base weird as a start. I haven't filled any records yet, I am still figuring out how to set up the fields. Your help is greatly appreciated.

---

### Post by katykat on 2010-12-18
I am a bookseller, and there is no question whatever that databases provide power and flexibility over spreadsheets. 

Though it should be noted that Amazon defaults to a CSV spreadsheet format, which seller databases are just beginning to adapt to. 

A good database should be able to *export* in a number of formats, especially one that is easily scriptable such as flat text which can be parsed by perl into MySQL format that can be used by websites. Some databases may be able to do this directly. 

Think about future usage. 

In the Win (and Mac)world there is commercial FIlemaker, which is a wizard driven database designer, that produces good results, but is hopelessly retrricted by its proprietary nature.
It also doesnt play well with ODBC drivers for scripting functions.

FIlemaker will load in Wine, but is extremely slow and kludgy. 

A good database will probably need to be built from Base on the Linux platform. The pre-made media databases, like Alexandria seem to be positively dreadful. We use Homebase2.3 from ABE (which is available for free to all) and while a seller database would work great for collectors as well. It is an Access97 Windows program, though does run well under wine (though the wine pages say it dont). 

The best databases are apparently relational SQL, but there has been little effort in making user friendly and easily configurable front ends for these. If anyone does know of any please post the name!

---

### Post by astrobob.tk on 2010-12-19
> **katykat said:**
> I am a bookseller, and there is no question whatever that databases provide power and flexibility over spreadsheets. 

Though it should be noted that Amazon defaults to a CSV spreadsheet format, which seller databases are just beginning to adapt to. 

A good database should be able to *export* in a number of formats, especially one that is easily scriptable such as flat text which can be parsed by perl into MySQL format that can be used by websites. Some databases may be able to do this directly. 

Think about future usage. 

In the Win (and Mac)world there is commercial FIlemaker, which is a wizard driven database designer, that produces good results, but is hopelessly retrricted by its proprietary nature.
It also doesnt play well with ODBC drivers for scripting functions.

FIlemaker will load in Wine, but is extremely slow and kludgy. 

A good database will probably need to be built from Base on the Linux platform. The pre-made media databases, like Alexandria seem to be positively dreadful. We use Homebase2.3 from ABE (which is available for free to all) and while a seller database would work great for collectors as well. It is an Access97 Windows program, though does run well under wine (though the wine pages say it dont). 

The best databases are apparently relational SQL, but there has been little effort in making user friendly and easily configurable front ends for these. If anyone does know of any please post the name!


I did't quite understand everything you mentioned, for am not knowledgeable about MySQL, but I must mention that I do use 2 main collection managers:

1. Alexandria: which you mentioned & which is limited to book collections
2. GCStar: which is a great collection manager for a variety of collections like movies, books, periodicals ....

both of these requires connection to retrieve details of the books which seems a good thing unless when you're not connected.

Am not sure if these would work with barcode scanners which would very much ease things. I don't own a barcode scanner but I am thinking of getting one specially that it is functional with online book managers like librarything.com

---

### Post by tgalati4 on 2010-12-20
If your collection is only a few sheets long, use a spreadsheet.  If it is greater than that, then use a custom package like alexandria, or create your own custom database using OpenOffice Base.

Music is simply managed by rhythmbox.  It scans a directory and creates a database automatically based on the music it finds.  You can search by artist, title, etc.  Oh, it plays music as well.

easytag also creates a database by reading music ID3 tags inside the mp3 file.  It allows you to correct bad data, add or change music genre and rename and move files around.

So for each category of "stuff" you want to manage, there are several tools that already exist.  Only in extreme cases would you need to make a custom database.

Don't forget to use a handy database to search for database tools:

apt-cache search book catalog

This brings up a few book/lending tools.  For instance opendb a web-based lending database.

Type in other search terms to find other types of tools.

---

### Post by astrobob.tk on 2010-12-20
> **tgalati4 said:**
> If your collection is only a few sheets long, use a spreadsheet.  If it is greater than that, then use a custom package like alexandria, or create your own custom database using OpenOffice Base.

Actually as I stated, I already use Alexandria & GCStar, but in the case of a fresh installation or reimporting the data back to the software(s) they aren't imported back as I edited them, particularly in Alexandria. If you have any particular tips, I would be thankful. Other particular help would be in dealing with smart libraries & in entries of books that I own both a physical & a digital version of.
As for the number of entries, they aren't great but I am thinking of the future as I am sure they will become greater.

> Music is simply managed by rhythmbox.  It scans a directory and creates a database automatically based on the music it finds.  You can search by artist, title, etc.  Oh, it plays music as well.

easytag also creates a database by reading music ID3 tags inside the mp3 file.  It allows you to correct bad data, add or change music genre and rename and move files around.Indeed, I use rhythm box & easytag as well. great tools :D
Mentioning music, I have most of my music as mp3 & some as flac. Do you suggest keeping them as mp3 or converting them to ogg ? I use sound converter for this.


> Don't forget to use a handy database to search for database tools:

apt-cache search book catalog

This brings up a few book/lending tools.  For instance opendb a web-based lending database.

Type in other search terms to find other types of tools.thanks for the command. That's something new I've learned :D

---

### Post by astrobob.tk on 2010-12-20
> **tgalati4 said:**
>  For instance opendb a web-based lending database.

Type in other search terms to find other types of tools.

I just checked opendb & downloaded the release but couldn't manage to know how I should work with it. How do I start after downloading the zip file ? I found no help online.

---

### Post by katykat on 2010-12-20
1. Alexandria: which you mentioned & which is limited to book collections
2. GCStar: which is a great collection manager for a variety of collections like movies, books, periodicals ....
---------------------------------------------------

Perhaps the best qustion is what you are trying to improve upon, as these tools seem to be working for you. 

To fully personalize a database the best option would be to write ones own, especially as then you could use scripts within to pull data from places like COPAC and ISBNdb.com. There is a neat perl module for the latter which pulls data directly from the API. Get a developer tag and you can pull data directly from the Amazon API, after spending a little time learning basic programming. 

However GCStar looks like a very nice collection manager. Is there any issues with it?

There is software which will allow you to use a cell phone as a scanner, but that is for a different purpose. Look to eBay for a cheap regular scanner. The most basic ones will simply emulate the keyboard. 

As far as books go, it would be nice to have a software which can be used not only from a collectors end, but also a sellers end if you should wish to sell off parts of the collection, after perhaps upgrading. A UIEE export capability would give alot of versatility. Unfortunately, the only software I have come across so far for this is written for Win.

---

