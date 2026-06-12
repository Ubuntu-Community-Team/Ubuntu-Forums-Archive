---
title: "How do I find out which character is missing (non installed font)"
date: 2011-02-16
forum: General Help
---

### Post by spaceshipguy on 2011-02-16
A client has sent me a docx. Actually it's not the first he's sent and it always causes me some kind of problems.

When I open the document (a normal boring 3 page text document) with Open Office some of the characters are replaced with little empty boxes. From context I suspect they are things like slashes and commas - but I don't know for sure.

I copy and pasted some into gedit and there they appeared as boxes with letters and numbers inside like FF04. 

Is there some way to find out what these symbols are?
I don't need to see them or print them, I just need to know if it is a plus sign, back slash, u with umlauts, or whatever.

Any suggestions would be gratefully received.:D

---

### Post by Vaphell on 2011-02-16
that number is the unicode number, you may try to look into the character map in Accessories menu to investigate (assuming that open office/gedit decoded it correctly)
or use the power of internet
[http://www.utf8-chartable.de/unicode-utf8-table.pl?start=65280](http://www.utf8-chartable.de/unicode-utf8-table.pl?start=65280)
eg. FF04 is described as FULLWIDTH DOLLAR SIGN
also try to select everything in the document and change the font, maybe you'll find one that covers the characters in question.

---

### Post by spaceshipguy on 2011-02-16
> **Vaphell said:**
> 
eg. FF04 is described as FULLWIDTH DOLLAR SIGN
.

Wow thanks, I'd never opened Character Map before - it looks cool.

Where do I type my four-digit unicode number to look it up?:D

edit----------

OK, I found [a place to look up unicode]("http://www.unicode.org/charts/").

---

### Post by Vaphell on 2011-02-16
you can use built-in find function in menus, not that it looks for codes only but it should return what you need.
there are also few sites that search in the unicode table eg.
[http://www.fileformat.info/info/unicode/char/search.htm](http://www.fileformat.info/info/unicode/char/search.htm)

---

