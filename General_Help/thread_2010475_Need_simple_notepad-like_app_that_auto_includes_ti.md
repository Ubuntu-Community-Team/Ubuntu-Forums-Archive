---
title: "Need simple notepad-like app that auto includes time/date upon every entry."
date: 2012-06-25
forum: General Help
---

### Post by papazulu on 2012-06-25
Is there a simple Notepad-like application in Linux that automatically includes a date a time tag to every entry you make.  E.g., it would look something like this:

Found solution to firefox slowness
6 / 25 / 12 --  3:45pm 

Couldn't remove System Reserved from launcher
6 / 25 / 12 -- 3:49pm

Discovered it was because I had inadvertently mounted it by clicking it open.  Restarted system, now it is gone.  Follow up on this later.
6 / 25 / 12 -- 3:58pm

etc. etc.  you get the idea.  It needs to be simple and notepad-ish.

---

### Post by sandyd on 2012-06-25
> **papazulu said:**
> Is there a simple Notepad-like application in Linux that automatically includes a date a time tag to every entry you make.  E.g., it would look something like this:

Found solution to firefox slowness
6 / 25 / 12 --  3:45pm 

Couldn't remove System Reserved from launcher
6 / 25 / 12 -- 3:49pm

Discovered it was because I had inadvertently mounted it by clicking it open.  Restarted system, now it is gone.  Follow up on this later.
6 / 25 / 12 -- 3:58pm

etc. etc.  you get the idea.  It needs to be simple and notepad-ish.
Try Tomboy

---

### Post by efflandt on 2012-06-25
This may not be elegant or optimized, but just a proof of concept for a shell script to sort of do that in a terminal.  Date is at the start of each note (you can format **date** differently) because it seemed more complicated to put it immediately after.  But I figured out how to get the cursor to the bottom of a text file automatically when opening **nano**.

```
#!/bin/sh
mylog=~/lognote.txt
[ -e "$mylog" ] && echo >> $mylog
date >> $mylog
echo >> $mylog
nano +`wc -l $mylog`
```Sample file:

```
Mon Jun 25 18:50:57 CDT 2012
Just a short note.

Mon Jun 25 18:51:17 CDT 2012
Another note later.
```

---

### Post by Habitual on 2012-06-26
> **sandyd said:**
> Try Tomboy
How is Ctrl+D "automatic" in Tomboy?

---

### Post by Habitual on 2012-08-16
I finally had to have this feature in a editor.
I now use Sublime Text2 with an F5 macro to insert the date/time. sure beats all the workarounds...

---

