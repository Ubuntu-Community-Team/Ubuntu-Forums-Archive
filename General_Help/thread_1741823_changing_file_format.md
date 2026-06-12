---
title: "changing file format"
date: 2011-04-28
forum: General Help
---

### Post by vivek.pandey on 2011-04-28
hey everyone
   say i have a pdf file and i want to change it to some other format defined by me which compresses the file to some ratio... how can i do that? also i would want it to retrieve it back.. so how can that be done?

thanx to all..

---

### Post by An Sanct on 2011-04-28
You can use file roller to create a [ZIP]("http://en.wikipedia.org/wiki/ZIP_%28file_format%29") or [7-Zip]("http://en.wikipedia.org/wiki/7-Zip") file (compressed) these can be decompressed afterwards, to produce the same file as before.

---

### Post by vivek.pandey on 2011-04-28
> **An Sanct said:**
> You can use file roller to create a [ZIP]("http://en.wikipedia.org/wiki/ZIP_%28file_format%29") or [7-Zip]("http://en.wikipedia.org/wiki/7-Zip") file (compressed) these can be decompressed afterwards, to produce the same file as before.

thanx for your answer.. obviously i know about zip files and other standard compressed files... i wanna have a compressed file of my own type with a ratio i want,,,

---

### Post by hwttdz on 2011-04-28
Well you just have to write your own compression and decompression algorithm.  

If this sounds intimidating, gzip, bzip2, and xz are some of the best.  And offer flags to control how aggressively they're compressed (at the cost of cpu time).  Unfortunately pdfs are generally pretty well compressed.  There are some other things you can do to them that slightly alter the document but occasionally provide pretty decent space savings: [http://astoryworthtelling.wordpress.com/2011/02/16/how-to-reduce-the-size-of-a-pdf-file/](http://astoryworthtelling.wordpress.com/2011/02/16/how-to-reduce-the-size-of-a-pdf-file/)

note that savings vary wildly based on input file.

---

### Post by An Sanct on 2011-04-29
Yes, media files, like jpeg, mpeg, mp3, ... etc will have very little benefit from compression...

By the way, what is the wanted result of your file altering???

Gaining space (compression) or making the file unreadable by others (encryption)?

IMHO, leave the compression part to the masters, there is no wheel to invent here for a "normal" person like myself for example. But when it comes to encryption, there is a lot of space for modification, you can use multiple encryption methods, to create your own custom format (with the existing algorithms)

---

### Post by vivek.pandey on 2011-04-29
> **An Sanct said:**
> Yes, media files, like jpeg, mpeg, mp3, ... etc will have very little benefit from compression...

By the way, what is the wanted result of your file altering???

Gaining space (compression) or making the file unreadable by others (encryption)?

IMHO, leave the compression part to the masters, there is no wheel to invent here for a "normal" person like myself for example. But when it comes to encryption, there is a lot of space for modification, you can use multiple encryption methods, to create your own custom format (with the existing algorithms)

my main motive is to learn to create my own file format.. there are lot of them for same file type say eg .txt , .odt,.docx,.rtf etc for a text or document say i am looking to do something similar.. and if together with it i can compress / encrypt.. that would be awesome....

---

