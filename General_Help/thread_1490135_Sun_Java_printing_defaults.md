---
title: "Sun Java printing defaults"
date: 2010-05-21
forum: General Help
---

### Post by dmolony on 2010-05-21
I have set up an HP 5M networked printer. The test page works fine, and the defaults are all set correctly. But when I try to print from my own java programs, the paper size is set to letter, and the margins are all set to 2.54 mm.

I can change the paper size to A4 (but I have to do it EVERY time). And the margins won't even let me change them. I type in 0, click in the next field, and the value changes straight back to 2.54.

It has been this way for at least the last two releases of Ubuntu.

---

### Post by lykeion on 2010-05-24
> **dmolony said:**
> [...]But when I try to print from my own java programs, [...]

Maybe I'm misunderstanding your question, but if you mean you have written your own Java code and having problems with orientation and setup margins, you could look up the Java tutorials on printing with Java:

[http://java.sun.com/docs/books/tutorial/2d/printing/index.html](http://java.sun.com/docs/books/tutorial/2d/printing/index.html)

---

### Post by dmolony on 2010-05-24
It is not my java code that is the problem, the exact same program runs perfectly on Mac and Windows. I suspect the problem lies with the Linux JRE, the code that runs PrinterJob.printDialog () behaves as I described above (which is obviously not what anybody would want).

---

### Post by lykeion on 2010-05-26
First of all it's hard to reproduce your error without any code samples.
And second I've no experience printing with Java, and even though ubuntu forums is large I guess you would be better off to try a more Java-specific forum to post this problem.

Like this post I found on Sun' (oops sorry Oracle's) Java forum:

[http://forums.sun.com/thread.jspa?threadID=5425072](http://forums.sun.com/thread.jspa?threadID=5425072)

---

### Post by Rimus on 2010-06-08
I have encountered the exact same problem, except my printer was Canon LBP2900 and not networked. I'm using the latest Sun Java from the repositories. There seems to be no way to change the default printing settings in the java dialog, because the dialog doesn't respect system defaults. (Nor can I share the code since it's a corporate app.)

 However, sometimes printing seems to work, but it's totally random. There should be a way always to "force print" on A4.

Unfortunately this bug makes Ubuntu/Linux pretty much unusable on a system that should be running a (badly coded) Java application. :sad:

P.S. I know I should be giving feedback to Oracle rather than writing to this  forum. In fact I'm currently looking for a way to do that, but the Sun Java site is way too crowded for finding any information...

Edit: Here is a thread from 2005 on the Java Programming forum about default page sizes:
[Java Programming [Archive] - Default page size for printing]("http://forums.sun.com/thread.jspa?forumID=256&threadID=650706")

---

