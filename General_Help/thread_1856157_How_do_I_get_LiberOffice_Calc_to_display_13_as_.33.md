---
title: "How do I get LiberOffice Calc to display 1/3 as .333333 instead of 01/03/2011?"
date: 2011-10-07
forum: General Help
---

### Post by Ulysses1994XF04 on 2011-10-07
I'm trying to write some graphs. Instead of taking all the time to type .333333333 or .142857429 I just want to type &quot;1/3&quot; and &quot;1/7.&quot;  The problem is, if I type &quot;1/3&quot; into a cell, it automatically coverts it to &quot;01/03/2011.&quot; Even if I type in a strange number like &quot;2/10.52,&quot; it automatically converts it to &quot;02/10/2052.&quot;   How to I get LibreOffice Calc to calculate 1 over a number instead of converting it into a date?

---

### Post by TeoBigusGeekus on 2011-10-07
Right click the cell>Format Cells>Number tab.
Select fraction.

---

### Post by Ulysses1994XF04 on 2011-10-07
Just did, but the problem is, it only works for that one cell.  I typed 1/4 in a cell and it stayed as 1/4, not as a date. But when I went to another cell and typed 1/5, it converted it to 01/05/2011. I reset that cell and then tried to do another cell. When I went to another cell though and typed 1/6, it came out as 01/06/2011.     Is there anyway to get it to make the Cell Format from Numbers to Fraction apply to all cells?  I have to reformat each one one at a time (because it's going to take me forever to do that; I have a lot of entries I have to type)?    Also, is there anyway to get it to automatically convert fractions to decimals numbers?   Is it possible to make it so that if I type 1/6, .166666666 appears in the cell?

---

### Post by Ulysses1994XF04 on 2011-10-07
Sorry the above post appears just as a giant block of text; I tried to break it up into smaller paragraphs in the edit function by hitting Enter and making some space between each, but the forums are compacting it together as one though

---

### Post by TeoBigusGeekus on 2011-10-07
Instead of selecting fraction, select number.
As for the your first question, select all the cells you want, or even the whole sheet, right click your selection and choose whatever appropriate.

---

### Post by Ulysses1994XF04 on 2011-10-07
Tried that, still having problems.

I highlighted all the columns on the screen and went to Format -> Cells. I reset it to Numbers. SOME numbers stay in the fraction form, but OTHER numbers still get automatically converted to dates for some reason.

Here are the numbers I want to type.

1/4.1
1/6.4
1/11.3
1/22.6
1/33.8

This is how they appear.

**_¼.1_**
**_01/06/2004_**
1/11.3
**_01/22/2006_**
1/33.8

I deleted everything, tried to reformat the cells again, but it still auto-converts those numbers to dates, and 1/4.1 into ¼.1.

What can I do? 

Also, like I said, can I get it to convert fractions into numbers? Can I type in 1/5 and get .2 to show?

---

### Post by bryanl on 2011-10-07
the issue may be that 1/3 is an operation, not a number.

to make it a number, you need to identify it as such. Try entering =1/3 and then the spreadsheet needs make no guess.

the format specification just defines how to show the item after it is entered. For instance, if you type 1/3, the guess is that you are typing a date in the current year or 1/3/2011 (depending upon how you have date formatting specified in the setup options). The inference of a date is also coupled with setting the format of that cell to show a date. If you change the format to number, you'll see 40546, which is the number of days since the reference date.

A fraction is a number written as a division. To get the spreadsheet to see it is a number, you have to tell it to do the division by putting the = in front of it during data entry. That makes it a formula to calculate rather than an expression to interpret.

---

### Post by Ulysses1994XF04 on 2011-10-07
> **bryanl said:**
> the issue may be that 1/3 is an operation, not a number.

to make it a number, you need to identify it as such. Try entering =1/3 and then the spreadsheet needs make no guess.

the format specification just defines how to show the item after it is entered. For instance, if you type 1/3, the guess is that you are typing a date in the current year or 1/3/2011 (depending upon how you have date formatting specified in the setup options). The inference of a date is also coupled with setting the format of that cell to show a date. If you change the format to number, you'll see 40546, which is the number of days since the reference date.

A fraction is a number written as a division. To get the spreadsheet to see it is a number, you have to tell it to do the division by putting the = in front of it during data entry. That makes it a formula to calculate rather than an expression to interpret.

well, =1/3 shows up as 12/30/1999 for some reason, but it does the calculation for all other numbers. I guess that'll work. Thanks!

---

