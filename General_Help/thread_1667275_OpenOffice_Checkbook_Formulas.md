---
title: "OpenOffice Checkbook Formulas"
date: 2011-01-14
forum: General Help
---

### Post by gerowen on 2011-01-14
I've got a spreadsheet that I use to keep track of my expenses and checking account balance.  Right now I have the following columns:

1) Date
2) Withdrawal
3) Deposit
4) Description
5) Balance

Then off to the side I've got two cells that keep track of my total withdrawals and deposits for that sheet(each month has its own sheet.)

I've got everything put in there so all I have to do is enter data and the spreadsheet formats it right when I tab over.  The only thing I can't figure out is the "Balance" block.  Every entry I have to manually enter the formula.  For example block E5 would contain:

=e4-b5+c5

Is there a formula or variables that I could include to have a generic formula that I could put in the whole column so that it would automatically do these calculations?

---

### Post by TeoBigusGeekus on 2011-01-15
If you select cell e1, click your mouse on its right bottom corner (where a little black square is) and drag it down to all the cells in the e column (without letting go of the left mouse button) the formula will repeat itself in all the cells.
You will have to do this only once, cause when you copy the whole sheet for the next month the formulas will be there.

---

