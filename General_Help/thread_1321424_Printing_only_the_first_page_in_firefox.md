---
title: "Printing only the first page in firefox"
date: 2009-11-10
forum: General Help
---

### Post by sokam on 2009-11-10
I am trying to print to pdf in firefox but continue to only manage to get the first page printed.  This seems to be a common problem.

I searched around the web and most people had a solution by editing their print.css file.  

I also found one that doesn't involve print.css.  I follow this thread and actually got my 2nd page print only if I highlighted the text I want to print and then go to option and check print selection.
[http://ubuntuforums.org/showthread.php?t=1278271](http://ubuntuforums.org/showthread.php?t=1278271)

However, in the same thread there also a link to another more elegant way of doing this but involve a print.css which it forgot to mention how I find this file in my directories.
[http://www.webdeveloper.com/forum/showthread.php?t=113600](http://www.webdeveloper.com/forum/showthread.php?t=113600)

Anyone can point me to the correct location of print.css file?  BTW, any fixes for this?

---

### Post by sokam on 2009-11-10
NO ONE can tell me?!

---

### Post by alphaniner on 2009-11-10
I searched my entire / and I don't have a print.css file.  Besides, the second link seemed to imply that the print.css method didn't work with Firefox.

> I had a @print called print.css which worked well for printing in IE and Opera, but not Firefox.

---

### Post by jnorthr on 2009-11-10
is there any way you can save the PDF while in firefox to a local drive ? Then you might be able to open the PDF using a ubuntu tool. Can't remember the name but something like 'evince' ? You may need to hunt around but i'm sure there is a tool to open PDF's provided in your ubuntu install.

---

### Post by sokam on 2009-11-14
I think my original thread created some confusion.  What happen is that anytime I just want to print out something from firefox that has more than one page, only the first page will print and subsequent pages are ignored.  

I checked "ALL PAGE" in option, and I try to "PRINT TO FILE" in the print option as well.  None work except if I highlighted all the text content and checked "Print selection" in print option, then it will print out multiple pages.

Alphaniner,

on the 2nd link I posted:
[http://www.webdeveloper.com/forum/sh...d.php?t=113600](http://www.webdeveloper.com/forum/sh...d.php?t=113600)

Yes, the person did say he had the same problem in the very beginning of the thread.  BUT if you read on you will find the follow and I quote:
>  To solve this, I placed the following in my print.css 
CODE:
[QUOTE]body { overflow-y: visible; }[/QUOTE]

Nonetheless, does anyone else had this problem at all?

---

### Post by sokam on 2009-12-09
Karmic Koala fixed this problem for me.

---

