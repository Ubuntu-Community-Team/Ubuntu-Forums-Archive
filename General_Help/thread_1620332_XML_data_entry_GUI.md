---
title: "XML data entry GUI"
date: 2010-11-12
forum: General Help
---

### Post by sbarmeier on 2010-11-12
Hi,

I am looking to create a large XML database, consisting of 2000+ main entries.

In particular, I am looking to create a database for Kanji flashcards by associating data (stroke count, radical, kun reading, on reading, etc.) to each Kanji. I will then typeset this database using TeX to obtain printer-ready flashcards.

I had a look at various XML editor (jaxe, xmlcopyeditor, conglomerate, mlview, etc.), but most of them really just feature syntax highlighting and validation. I am looking to create some GUI which will make the data entry as smooth as possible. One possibility might be to write an HTML form, which then writes the entered data to a file via some 'Submit' button.

Still, I thought that with a popular format such as XML there might be configurable data entry tools available. (Maybe comparable to iTunes's MP3-tag window, where there is a small form which allows you to enter artist, title, track no., etc., with a next button taking you to the next track to edit.)

I'd be grateful for any ideas helping me create a large document consisting of entries looking roughly like

<card number='1'>
<kanji>&#29983;</kanji>
<radical></radical>
<strokecount>5</strokecount>
<kun>&#12394;&#12414;&#12288;&#12356;&#12539;&#12365;&#12427;</kun>
<on>&#12475;&#12452;</on>
</card>

<card number='2'>
...
</card>

Many thanks.
Sev

---

### Post by sbarmeier on 2010-11-14
It seems I will answer my question myself...

XML data entry is indeed not done via XML editors but via database frontends. According to the data you wish to enter and how often you anticipate to need to update the data you might wish to run some sort of SQL server (PostgreSQL, MySQL, SQLite, etc.) and build a custom frontend yourself with tools like Glom, Knoda, Kexi or Bond. (Just be prepared to convert the data from their respective export formats, most often CSV.)

There is also a customizable XML database manager (thought for collections of CDs, Stamps, etc.) which lets you define your own collection style, but you need KDE...

Anyway, since this post seems to be the only thing coming up for "XML data entry ubuntu", I hope someone will find what they're looking for...

---

