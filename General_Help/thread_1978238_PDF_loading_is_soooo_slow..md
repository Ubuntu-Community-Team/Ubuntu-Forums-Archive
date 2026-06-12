---
title: "PDF loading is soooo slow."
date: 2012-05-11
forum: General Help
---

### Post by rasmus91 on 2012-05-11
Hey everyone.

Im on a laptop, with only ubuntu on it. Everything runs smooth and fast, except pdf loading. its a drag.

It has a Core i5 2.5 ghz processor as well as 4 Gb's of Ram, and it literally takes 3-12 seconds to load a pdf page. In my honest opinion that is bogus! when i had windows on this laptop i could load a pdf in 0.5 secs. i haven't encountered this problem before in Linux, but it really bugs me.

any help will be appreciated.

---

### Post by AnotherMuggle on 2012-05-11
Actually I noticed this last night.  A two page PDF document took so long to load I started wondering if it had crashed.  This is on an i3 Desktop with 4GB RAM, so it is a plenty capable machine.

---

### Post by MG&amp;TL on 2012-05-11
...that shouldn't happen. Have you tried a different pdf viewer? Also, is it just file loading, or pdf in particular?

---

### Post by AnotherMuggle on 2012-05-11
> **MG&TL said:**
> ...that shouldn't happen. Have you tried a different pdf viewer? Also, is it just file loading, or pdf in particular?

I haven't noticed any other speed issues, just PDF.  The viewer opened and displayed "Loading..." in the top(?) corner for a long time before the document appeared.  I also noticed that resizing the window made it take just as long for the document to render again.

---

### Post by rasmus91 on 2012-05-11
> I haven't noticed any other speed issues, just PDF. The viewer opened and displayed "Loading..." in the top(?) corner for a long time before the document appeared. I also noticed that resizing the window made it take just as long for the document to render again.

exactly.

and yes, i have tried the standard one as well as okular. same story.

---

### Post by GonchuB on 2012-05-11
Try reconficuring the evince package:

open terminal:

```
sudo dpkg-reconfigure evince
```

then move the pdf to your Desktop and do:

```
evince ~/Desktop/nameOfPDF.pdf
```


hope it helps

---

### Post by traditionalist on 2012-05-11
This seems to be standard, some PDF's take an age to load. I have not found any way to speed them up, although I had the same problem on Windows 7.  I have a fairly powerful machine as my main machine but it doesn't make much difference.

If you use PDF's a lot install the new Calibre, it is much faster than the native viewers etc;

[http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux)   the newest version is also otherwise very good indeed.

Regards....Trad

---

### Post by rasmus91 on 2012-05-11
will check it out.

Just found out that i am unable to edit my char sheets properly in The standard document viewer. And not at all in any of the others. anyone know a good pdf viewer that can edit empty field, as well as do the auto calculations?

---

### Post by traditionalist on 2012-05-11
> **rasmus91 said:**
> will check it out.

Just found out that i am unable to edit my char sheets properly in The standard document viewer. And not at all in any of the others. anyone know a good pdf viewer that can edit empty field, as well as do the auto calculations?

Calibre!  :)

[[IMG]http://img213.imageshack.us/img213/1598/calibre.th.png[/IMG]](http://img213.imageshack.us/i/calibre.png/)

You might also find this useful;

[http://live.gnome.org/PdfMod](http://live.gnome.org/PdfMod)

Regards...Trad

---

### Post by rasmus91 on 2012-05-11
> Calibre! 

which seems to be even worse than the original one :/ I will give it a couple of tries though, im just annoyed right now that it has to be this hard to get something like a simple PDF to open properly.

okay, so "view" appearently opens the document with Acrobat reader for some reason... THis program seems to be able to upload the file to a ebook reader, but what i am looking for is a proper way to edit formfillable fields in a pdf and save it. much like Foxit reader in windows, except on ubuntu.

---

### Post by kuifje09 on 2012-05-11
Strange behaviour.  When I load a pdf of 3.5MB  then evince 2.32.x  does open and show the page whitin a second.
This one : [http://www.uni-trend.com/ut70a.html](http://www.uni-trend.com/ut70a.html) then download the manual as test.
Its about a multimeter ( electronics ) A reference is always nice..

---

### Post by rasmus91 on 2012-05-11
Anyways, installed Foxit reader in wine, and it seems to work perfectly.

---

### Post by eggsbenedict on 2012-05-14
I'm having this same issue too.  I have a dual boot Ubuntu 10.04 and 12.04.  Opening PDFs in 10.04 is pretty smooth and fast, but PDFs in 12.04 take forever to load for me.  

I'm trying to slowly go toward 12.04, but I'm finding little annoying things in 12.04 that I'm trying to solve before wiping my HDD and doing a clean install of 12.04. 

I've tried the calibre program on 12.04, but they don't seem to load more quickly.  Am I doing something wrong? :-S

Thank you!

---

### Post by AnotherMuggle on 2012-05-15
> **eggsbenedict said:**
> I'm having this same issue too.  I have a dual boot Ubuntu 10.04 and 12.04.  Opening PDFs in 10.04 is pretty smooth and fast, but PDFs in 12.04 take forever to load for me.  

I'm trying to slowly go toward 12.04, but I'm finding little annoying things in 12.04 that I'm trying to solve before wiping my HDD and doing a clean install of 12.04. 

I've tried the calibre program on 12.04, but they don't seem to load more quickly.  Am I doing something wrong? :-S

Thank you!

I don't think you are doing anything wrong.  My guess is there is a bug, or just a bad code change, which has snuck into a core pdf library somewhere.  This would cause any software dependant upon that library to suffer the same symptoms.  I am sure one of the devs will fix it soon, especially with 12.04 being an LTS release.

---

