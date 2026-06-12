---
title: "Consolidating Bookmarks in Firefox"
date: 2010-03-14
forum: General Help
---

### Post by opethfan89 on 2010-03-14
Hi all,

I have about 5 years worth of old bookmark backups that I haven't had a chance to sort through. Everytime I wipe out my computer, I backup the bookmarks, or everytime I make a major backup, etc. I got through SOME of the bookmarks, as far as sorting them, but it is almost overwhelming.

Is there any program that will allow me to combine all my .html files, purge the duplicate links, and maybe even check the links to see if they still work?

Thanks for any advice, and sorry if this topic has been covered elsewhere. I have spent HOURS googling but nothing is looking to do what I want (which is, basically, everything!)

Thanks,
Opethfan89

*Edit* Well, I suppose I can use AIM-Deadlink to detect dead links, and then something like Bookmark Duplicate Detector to delete duplicates, but I still need a program to merge all of my bookmark.html files!

---

### Post by lovinglinux on 2010-03-15
> **opethfan89 said:**
> *Edit* Well, I suppose I can use AIM-Deadlink to detect dead links, and then something like Bookmark Duplicate Detector to delete duplicates, but I still need a program to merge all of my bookmark.html files!

Firefox doesn't store bookmarks on html files anymore, but on an sqlite database. 

You could import each html file and use the Bookmark Duplicate Detector to remove duplicates. If you have a lot of html files, you make a script to merge them, then import.

---

### Post by opethfan89 on 2010-03-15
> **lovinglinux said:**
> Firefox doesn't store bookmarks on html files anymore, but on an sqlite database. 

You could import each html file and use the Bookmark Duplicate Detector to remove duplicates. If you have a lot of html files, you make a script to merge them, then import.


Can you elaborate on how to make the script? I'm not exactly as programming-savy as I used to be.

---

### Post by lovinglinux on 2010-03-15
> **opethfan89 said:**
> Can you elaborate on how to make the script? I'm not exactly as programming-savy as I used to be.

You could try to use cat command to join the html files like this:

```
cat bookmarks1.html bookmarks2.html bookmarks3.html > allbookmarks.html
```

Keep in mind that I don't know if this will work well, since each bookmark file has it's own top level tags. I'm not sure if they can be repeated and if the importer will parse them correctly. Nevertheless, you could use sed (see man sed) to remove and replace duplicated lines.

Another option would be to use iMacro extension for Firefox in order to create a macro that will grab each html file and import using the bookmark manager.

---

### Post by opethfan89 on 2010-03-18
> **lovinglinux said:**
> You could try to use cat command to join the html files like this:

```
cat bookmarks1.html bookmarks2.html bookmarks3.html > allbookmarks.html
```Keep in mind that I don't know if this will work well, since each bookmark file has it's own top level tags. I'm not sure if they can be repeated and if the importer will parse them correctly. Nevertheless, you could use sed (see man sed) to remove and replace duplicated lines.

Another option would be to use iMacro extension for Firefox in order to create a macro that will grab each html file and import using the bookmark manager.

Thanks Lovinglinux, I have some free time today and tomorrow so I will experiment with this and post back. If worst comes to worst, I may just end up deleting those old bookmarks. I've changed so much in that many years that I don't like anything from back then (music/fashion-wise).

Thanks again.

---

