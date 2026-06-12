---
title: "How to use formulas in OneOffice.org Spreadsheet"
date: 2010-12-29
forum: General Help
---

### Post by WlaadDyaab on 2010-12-29
Hi

I'm trying to create a simple times table on OpenOffice.org Spreadsheet

I'm trying to use the "$" in the top tab (input line) i.e. > =A3*$B2$
> =A3*$B3$
> =A3*$B4$
...etc

or

> =$A3$*B2
...etc


It makes (or it's meant to make) the top column the default kind of numbers that the first row of numbers should multiply by it, or that's how it is in Microsoft Excel

To make the question clearer. When I used to use Microsoft Excel in Windows I would do just as I said in the above and I would be able to construct simple multiplication tables to more bigger/harder to memorize kind of type. And that would be by dragging the rectangle from it's bottom-right corner

[ATTACH]179641[/ATTACH]

[ATTACH]179643[/ATTACH]

So my question is what's the alternative OpenOffice.org Spreadsheet symbol for the "$" symbol used in the formula bar in Microsoft Excel?

Thanks

---

### Post by noah++ on 2010-12-29
The **$** operator fixes the column letter or row number that immediately follows it, so that when you do the dragging you describe, the program doesn't try to change it dynamically per-cell. It makes these column or row values *absolute references*. It kind of does the opposite of what you seem to think it does, and it works the same in Excel as in OpenOffice.

So if you just want to copy the formula through the whole row or column with automatic changes, just omit the **$ **operators from the formulas entirely. If you do want to fix a row or column value, the **$ **precedes that value in the formula. Omit the trailing **$**.

---

### Post by WlaadDyaab on 2010-12-29
[SOLVED]

Oops Sorry!!

I got the whole thing wrong way round

I just seen this tutorial:

[http://www.youtube.com/watch?v=cBcDnHu9zQw](http://www.youtube.com/watch?v=cBcDnHu9zQw)

The Dollar symbol is actually inserted this way:

e.g.

> =A3*[COLOR="Red"]$[/COLOR]B[COLOR="Red"]$[/COLOR]2

Not how I posted earlier:

> =A3*$B2$

Sorry my bad. Nothing wrong with OpenOffice Spreadsheet Lol!!

---

### Post by noah++ on 2010-12-29
OK, cool. Hope it's clear what **$ **truly does, too.

---

### Post by WlaadDyaab on 2010-12-29
Thanks mate very appreciated

I corrected myself after watching the YouTube link above

It just me being a klutz Lol

Thanks for the reply

---

