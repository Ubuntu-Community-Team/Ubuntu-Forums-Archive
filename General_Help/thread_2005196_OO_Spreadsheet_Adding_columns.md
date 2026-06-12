---
title: "OO Spreadsheet: Adding columns"
date: 2012-06-17
forum: General Help
---

### Post by bergspyder on 2012-06-17
This isn't right forum for my question but having had no success on OO forums, I'm hoping someone here can help out:

I have very large ODS file converted from MS Excel a couple of years back. OK, a couple of Excel functions didn't work properly in OOCalc -- particularly conditional formatting -- but it worked well.

Then one day I needed to add several columns before existing column A in one sheet, normally a very simple operation. But problem is, when new columns inserted, it changes formatting in all previous columns (Excel doesn't). To refomat all previous columns back to what they were will take hours.

Help anyone?

---

### Post by audiomick on 2012-06-17
That is extremely odd. What you describe is exactly the reverse of what should happen, i.e. select the number of columns you want to add by clicking on the head of the left most column and wiping across the number of columns you want to add, then right click and add columns. I expect you know this if you are working with such large tables. Anyway, the new columns should have the formatting of the columns that were selected. I have done this any number of times and never had a problem with it. My sheets aren't all that complicated though.

I would try the following  two things as a way of trying to get around the odd behaviour.

One would be to create a new, empty sheet, and try and copy the contents of the old sheet into the new one with a few spare columns on the left.

Another would be to copy only the sheet in question into a new file and see how it behaves there. To do this, create a new file, go to the existing file and right click on the tab at the bottom of the sheet. Use the "move / copy sheet" option, and be careful to check the "copy" box or the sheet will be moved out of the existing file into the new one. The reason for trying this is that I sometimes have the feeling that OO does get a bit odd in it's behaviour when files get very large, or when there are a lot of instances of OO open at the same time.

---

