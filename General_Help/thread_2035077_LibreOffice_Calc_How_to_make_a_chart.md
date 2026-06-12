---
title: "LibreOffice Calc: How to make a chart?"
date: 2012-07-29
forum: General Help
---

### Post by Kelvari on 2012-07-29
I'm trying to make a chart off of some data that I've got, but I'm not getting a chart that shows any data at all. Is there a tutorial or something that I can use?

Steps that I've been following:
1. Highlight desired data area in spreadsheet
2. Click "Chart" button
3. Select chart type
4. Re-enter data range (A1:H31, Data series in columns, first row as label, first column as label)
5. Click "Add" as the data series window comes up blank. Set B1 as the name, B2:B31 as the Y Value. 
6. Set Categories from $Sheet1.$A$1:$H$31 to $Sheet1.$A$1:$A$31
7. Repeat step 5 for all remaining data sets
8. End up with a blank chart

I'm pasting in the data from [here]("http://w3schools.com/browsers/browsers_os.asp")

---

### Post by Vaphell on 2012-07-29
you have to make sure that the data is recognized as numbers - you can't graph text

i managed to produce a tidy chart based on these tables.
1. copy-paste the data to gedit
1a. optional, depending on locale: replace all dots to locale defined separator (colon in my case)
2. copy-paste from gedit to calc, in the paste dialog select tab as delimiter and enable recognizing numbers.

now the data should be in numeric format.


ps. why on earth did they use months in reverse order?

---

### Post by Kelvari on 2012-07-29
Thank you for those directions. Seems to have worked.

As far as why they put the dates in reverse order, I'm guessing to show the most recent trends first? Would be easier to make the charts properly if they put them in chronological order, though.

---

### Post by vasa1 on 2012-07-29
One more point, somewhat related, is that many sources format their data in such a way so as to render numbers as text. I don't know why.
LibreOffice Calc has a nice feature that helps interpret numbers as numbers: "detect special numbers".
Unfortunately, you have to tick that option each time you do a "text import".

Oops: covered by Vaphell already!

---

