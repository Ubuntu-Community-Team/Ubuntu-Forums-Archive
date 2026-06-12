---
title: "How can I organize this data? Using a database?"
date: 2011-11-23
forum: General Help
---

### Post by El Potro on 2011-11-23
Hello everyone,

I have a lot of texts and books I've read here on my house, and what I want is to systematise them in a list or database (I don't know how should it be called). In order to be able to type the name of the author, and get all the names of the books that I have from this author, their years of publication, and other complementary data that belongs to each book. Or maybe type a year, and get a list of all the books that I have, that have been published in that year.

How can I do this? I ask this here because I have never used databases, nor I have any clue of how should I do this.

Can anybody please help?

Thank you very much in advance!

---

### Post by rewyllys on 2011-11-23
> **El Potro said:**
> Hello everyone,

I have a lot of texts and books I've read here on my house, and what I want is to systematise them in a list or database (I don't know how should it be called). In order to be able to type the name of the author, and get all the names of the books that I have from this author, their years of publication, and other complementary data that belongs to each book. Or maybe type a year, and get a list of all the books that I have, that have been published in that year.

How can I do this? I ask this here because I have never used databases, nor I have any clue of how should I do this.

Can anybody please help?

Thank you very much in advance!
A quick-and-dirty way of doing what you want would be to put your book data into Tomboy Notes.

Involving somewhat more effort, but probably yielding more satisfactory results in the long run, would be to use LibreOffice Base.  Using LOB means that you would need to decide in advance what kinds of searches you will want to make: e.g., by author, by title, by year, etc. 

The "etc." part is what you need especially to think about.  Will you want to search hardbacks vs. paperbacks? personal notebooks? publishers? languages? . . . ?

Once you're reasonably sure that you've decided what kinds of searches you'll be wanting to make, you'll find that the Wizards in LOB will be very helpful to you in setting up your database.

Good luck.

---

### Post by Hadogenes on 2011-11-23
I really like to use Calibre to organize all of my e-books.  If you're talking about actual physical books, I use LibraryThing to keep track of everything.

Calibre can be found here: [http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux)
And LibraryThing here: [http://www.librarything.com/](http://www.librarything.com/)

Good luck!

---

### Post by oldfred on 2011-11-23
I have not used either of these, but they look interesting for a prebuilt database for exactly what you want.

Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/)

---

### Post by dragonfly41 on 2011-11-23
A couple more suggestions ...

Depending on the scope of your collections ...

[http://www.zotero.org](http://www.zotero.org) is a useful Firefox add-on which creates a database in Firefox profile and syncs with zotero cloud server.

I have also sync'd with a local host Apache through WebDAV which allows private collections to be managed.   There is a PHP script for this purpose ..  

phpZoteroWebDAV

discussed here .. [http://forums.zotero.org/discussion/4736/2/php-based-webdav-server-can-be-used-with-any-eg-free-hosting-plans-and-via-standard-ports/](http://forums.zotero.org/discussion/4736/2/php-based-webdav-server-can-be-used-with-any-eg-free-hosting-plans-and-via-standard-ports/) 

...

For _very large_ collections [http://www.exist-db.org](http://www.exist-db.org) uses XQuery.   

eXist runs either stand alone or on Tomcat.   Probably overkill for your needs.

---

### Post by oldtimer7777 on 2011-11-23
Tellico

> **El Potro said:**
> Hello everyone,

I have a lot of texts and books I've read here on my house, and what I want is to systematise them in a list or database (I don't know how should it be called). In order to be able to type the name of the author, and get all the names of the books that I have from this author, their years of publication, and other complementary data that belongs to each book. Or maybe type a year, and get a list of all the books that I have, that have been published in that year.

How can I do this? I ask this here because I have never used databases, nor I have any clue of how should I do this.

Can anybody please help?

Thank you very much in advance!

---

### Post by lswb on 2011-11-23
For a personal collection you could probably work up your own system using a variety of database or spreadsheet software. If you do a name & description search of the repositories for "ISBN" (the standard publication identification system) you'll find a few programs listed including Alexandria & bibshelf. Never tried them myself so I can't give a testimonial. Some kind of wiki program may suit you, too.

---

