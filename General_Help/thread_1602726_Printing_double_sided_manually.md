---
title: "Printing double sided manually"
date: 2010-10-21
forum: General Help
---

### Post by futterwaken on 2010-10-21
Hi there people.

I'm not sure this is the proper place to post  this issue. If you think this should go to another section, please let  me know - I'll move it.

**Intro**
I bought a graphical  calculator for my daughter. I want to print the calculator's manual, or  at least part of it. But i want to spend the least ink and paper  possible.

**The work**
So i wanted to print two pages on  each side of a A4 sized piece of paper (about the same size as a  "Letter" format - give or take), totalling 4 pages at A5 size (half an  A4) . 

Also, i want to match the front side of the paper with the back side so  that if the front has page 1, the back has to have page 2.
I hoped by  combining front/back as pages 1/2, 3/4, 5/6, and so forth, that in the  end i could cut the printed papers and make a book...

**The equipment**
I have a printer shared from a "old" machine with ubuntu 10.04 via smb.
I'm printing from another machine that also has ubuntu 10.04.
The document is a PDF and i'm using evince (Document Viewer 2.30.3).
I'm using CUPS 1.4.3-1ubuntu1.2
(all packages are stated as up-to-date)

**The Job**
I already checked the quality of the result on my printer at that size (even in draft mode) and it's good enough.

Since my printer doesn't feature double sided printing i have to do it manually.
(How hard can it be?)
I  found on the printers properties an option to print "a number of pages  per side" and another option to "print only the odd pages" or "the even  pages".

So it looked like a two phased job.
It all seemed perfect but it doesn't work! At least for what i want to do....
(thank god i just  tried to test this with the first 12 pages: the document has about 400!)

**The problem**
So why it doesn't work?

Because when i choose [two pages per side] and [print only the **odd** pages] i get:
pages 1 and 2, side by side, on one paper
and then
pages 5 and 6 on another
and then (9 and 10), and then (13, 14), etc....
===Notice that i get odd and even pages but it skips every other pair===

Then, when i tell it to print [two pages per side] and [print only the **even** pages] i get the **other** set of pairs, namely:
pages 3 and 4 on one paper
then 7 and 8, then 11 and 12, etc...

So  if i tried to the feed sheets from the first printing phase to the  second, i would get page 3 on the back of page 1 and page 4 on the back  of page 2, etc... Well, that's not what i want!

Then i found out a  page printing order: "left to right" or "right to left". So i figured  that the second phase ought to go "right to left" to solve the issue...
(Thankfully, this time i picked up a piece of paper and a pen and started to project the job...)

**The Bug**
Then i got to the "eureka!" part: Of course it doesn't work!
Think  for a minute: If pages 1 and 2 get printed on the same face of the same  piece of paper how can they ever be printed back to back???

Further,  if you come to think, when you choose to print "only odd pages" or  "only even pages" and you get odd and even pages at the same time...  well, that's a bug.

What's wrong is that the odd/even page  "filtering" is made after the pages are layed out by the "two pages on  the same face" routine...

I could get around this issue if i  could select just the odd or the even pages in "page range", but it only  allows ranges like "1-3" or "10-20" or sets like "1,3,5,7,9" and the  text is about 400 pages, ... i'm not going that way...
It's a no-go for this project!

**Conclusion**
Shamefully  (i'm rather annoyed with this!!!!) i had to do it from my laptop, which  has Windows 7 and it has basically the same options for printing, only  they're working properly!
And yes, it was printed on the same printer "served" by that ubuntu "old" machine!

Guys, sorry for the long text.
Every comment is welcome.

Regards,

Futterwaken

---

### Post by wolfgangmcq on 2010-10-21
Perhaps you should submit a bug report to [http://bugs.edge.launchpad.net/ubuntu/+filebug](http://bugs.edge.launchpad.net/ubuntu/+filebug)? That **does** sound annoying...

---

### Post by efflandt on 2010-10-21
If you actually want to have it so you can staple down the middle like a booklet with half size pages (instead of stapling top, corner, or one side), you may have to recompose the original document so pages are in the proper order.  That is what is done for our employee directory.  But even with a duplex printer I first have to practice with a couple of pages to make sure I did everything right (landscape with pages right side up on each side.  But actual page order in the original file is:

Side 1: Last page - Page 1

Side 2: 2nd last page - Page 2
_

Side 3: 3rd last page - Page 3

Side 4: 4th last page - Page 4
_

and so on.  Then you can vertically staple it down the middle like a booklet.

---

### Post by futterwaken on 2010-10-22
> **wolfgangmcq said:**
> Perhaps you should submit a bug report to [http://bugs.edge.launchpad.net/ubuntu/+filebug](http://bugs.edge.launchpad.net/ubuntu/+filebug)? That **does** sound annoying...

Thank you for pointing me in the right direction wolfgang, i'll file this bug there.

Regards,
Futterwaken

---

### Post by futterwaken on 2010-10-22
> **efflandt said:**
> If you actually want to have it so you can staple down the middle like a booklet with half size pages (instead of stapling top, corner, or one side), you may have to recompose the original document so pages are in the proper order.  That is what is done for our employee directory.  But even with a duplex printer I first have to practice with a couple of pages to make sure I did everything right (landscape with pages right side up on each side.  But actual page order in the original file is:

Side 1: Last page - Page 1

Side 2: 2nd last page - Page 2
_

Side 3: 3rd last page - Page 3

Side 4: 4th last page - Page 4
_

and so on.  Then you can vertically staple it down the middle like a booklet.

Actually, that's a very good idea efflandt.

Since i'm doing this at home, in practical terms stapling it like a leaflet would not be practical for the entire manual because, even using 4 pages per sheet, on a 400 page manual that would lead me to an 100 sheets stapling task with a specially long stapler.

One way to get it would be to organise the manual into several booklets using that technique and then join them... i believe that most books are made that way.

Although i already got the job done, it's most likely that idea will come handy in the future.

Thank you for that tip.

Regards,

Futterwaken

---

