---
title: "OpenOffice Base Navigation and Display very slow"
date: 2011-03-31
forum: General Help
---

### Post by col48 on 2011-03-31
I have set up an OpenOffice (3.2) Base database - tables, mainly, and a few queries.  The main table contains about 9000 rows and around 50 fields and there is a second table of 1900 rows and 20 fields and a few other tables with either fewer rows or many fewer fields.  The primary key on the main table is a single text field.  The .odb file is 4.4Mb.

There are no Forms or Reports; the idea at the moment is that I enter data using OO's Table data view.  I see that I have an embedded HSQL database and I cannot change Edit>Database>Properties because it is greyed out.

Opening the database is reasonably quick (about 5 sec) but then when I want to look at any but the smallest of tables (in data Table view) it is very slow (15 sec on the main table) to display the first group of rows.  When I want to move to show a different record it takes just as long to display the new set of rows. It makes no difference whether the new set of records is adjacent (in terms of record order) or a long way off.

[COLOR="Blue"]I need to speed this up x3 or more or I will have to abandon Base as impractical to use.
[/COLOR]
On the OO Forum some posts talk of separating the database from the engine and others of increasing the cache size. I can't do the latter as access is via the greyed out option and I can't find any instructions for the former. I'm not convinced these would have much effect anyway.

Has anyone hit on any tricks which would help?

---

### Post by Hagar Delest on 2011-03-31
Instead of the Ubuntu version of OOo, you can try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

It may help to start with a new profile, restore it if it doesn't improve anything. See how to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403). But don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by col48 on 2011-04-04
Hagar

Thanks for the suggestion.  Unfortunately refreshing the profile made no difference.

I had the same database in OO 2.4 on my Hardy system (ie the same data except for a few fewer rows in some tables but exactly the same table structure) and it was also slow but not *_this_* slow.  I populated the OO 3.2 database by transferring the data as csv files.  No reason for the new database to be 'contaminated' by any incompatability issue.

[I was away for a few days so only saw your response an hour ago]

How would the vanilla version help?  I'm not using any sophisticated features in any case.

---

### Post by Hagar Delest on 2011-04-04
The Ubuntu version is based on the go-oo version from Novell, some packages may also be tweaked (some distros do it). So there are more features but sometimes more bugs. That's why the vanilla version can sometimes be quicker or less buggy.

---

### Post by col48 on 2011-04-05
Now that makes sense!

I'll make the move in a week or so - I'm under time pressure at present.

---

### Post by giuliano1969 on 2011-08-24
The problem arise from the Java JRE version installed.

Please check
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/724217](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/724217)

and provide a new installa of java JRE

It will be MUCH faster...

---

### Post by Lantau on 2011-12-30
The problem still exists on JRE_26 and Libre Office in Ubuntu 11.10.

The following link, referenced in post #17 of the bug report, is the easiest solution I found. It also keeps the later version of JRE for other applications.


[http://hardc0l2e.wordpress.com/2011/04/05/libreoffice-openoffice-base-slow/]("http://hardc0l2e.wordpress.com/2011/04/05/libreoffice-openoffice-base-slow/")

---

