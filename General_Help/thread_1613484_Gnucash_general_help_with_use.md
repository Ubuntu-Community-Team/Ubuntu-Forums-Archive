---
title: "Gnucash general help with use"
date: 2010-11-04
forum: General Help
---

### Post by claven123 on 2010-11-04
I'm in the process of converting my 10+ year quicken file to gnucash (gosh help me).  Well, so far it's going better than I thought.  I actually like this program so far.  I've been able to download transactions from my main bank etc.. and reconciled a few accounts.

I've wrapped my head around the double entry thing and doing good.

My main question for those who have used this and know....

I've moved the checking account to assets 
When I write a check or spend money I transfer the funds from checking to the store...
I track this with an expense account, say expenses:Other spending or what ever....

What happens to the account [Other spending]?  does it just keep growing and growing, where does it fit into the budget concept and does money ever flow OUT of it?


The other question involved credit card transactions....

I noticed in the help areas it says to set up an expenses:Interest account to transfer money from the credit card to the expenses:Interest.  Does this account get used for all the credit cards?  Does it just keep growing and growing?

The same with charges on the credit card.  What account do I use?  The help files say to use the same expense accounts you would use for regular purchases from banks etc...


Thanks,

---

### Post by claven123 on 2010-11-06
Is there a gnucash forum, I know they have the the listserv mailing set up.  Is that the best way to get info and help with gnucash?

---

### Post by junapp on 2010-11-06
> **claven123 said:**
> 
What happens to the account [Other spending]?  does it just keep growing and growing, where does it fit into the budget concept and does money ever flow OUT of it?
I'm only chirping in here because you haven't got much response - I'm not an expert, but essentially  I believe the answer is yes, it keeps growing and growing until you close the particular accounting period, resetting it back to zero for the next accounting period. I'm not familiar with GNUCash's method by which it does this, I suspect a gl entry of some sort.

maybe this might shed some light:
[http://www.quickmba.com/accounting/fin/closing-entries/](http://www.quickmba.com/accounting/fin/closing-entries/)
I don't know how much of this GNUCash does for you in the background.
see also:
[http://www.quickmba.com/accounting/fin/double-entry/](http://www.quickmba.com/accounting/fin/double-entry/)

old svn entries for gnucash indicate that there may be some support for this:
[http://svn.gnucash.org/docs/head/bookperiods.html](http://svn.gnucash.org/docs/head/bookperiods.html)

and in even more to the point form:
[http://gnucash.1415818.n4.nabble.com/Closing-the-Books-td1429434.html](http://gnucash.1415818.n4.nabble.com/Closing-the-Books-td1429434.html)

---

### Post by junapp on 2010-11-06
> **claven123 said:**
> Does this account get used for all the credit cards?
The same with charges on the credit card.  What account do I use?  
Some of that would be personal choice. You could have one account called "bank charges", or a separate account for each card and each bank. It would all depend on the level of detail you want to report on, but also the level to which you want to record details. I suspect you may want an expense account for bank charges, and maybe another for interest expense, but I'm only basing that on your questions. For some companies, I've seen it done where they they wrap it all in a "General and Admin" expense account as they are not interested in capturing that much detail in their accounting books. They have no requirement for knowing how much interest was paid on each card in a given period. It ends up being completely immaterial to the other expenses, thus unnecessary to capture and report on separately.

---

### Post by claven123 on 2010-11-06
I guess one of my issues is that I have 10+ years of data.  Some of the accounts have been closed for years and are inactive and a couple of cards I have had for this span of time.

I have set up expense:CC Fees and Expenses:Finance Charge  which is all fine, but what happens on the other side...  do these amounts to increase over time and how does this impact the overall net worth?  That is my big question.

If I hide and account the amounts still seem to contribute to the sums at the bottom.

In quicken I didn't track too many categories and just used a few major ones... one big one was "other spending" which was almost everything besides groceries, gas and bills.

So, will this "other spending" account just get bigger and bigger, and does it contribute to my total net worth or make it worse?

Thanks for the information, and I'll have to check out the sites.

---

### Post by junapp on 2010-11-07
No, they get set back to zero (along with your income accounts) when you "Tools -> Close Book" which you should be doing at say tax time at least. The difference of income and expenses when you do that will likely fall into something like equity or retained earnings. 

As for the multiple years of data, I wouldn't bother importing all the data, just the balances for the day you start using GNUCash and move forward from there. Unless I'm missing something.

You may want to make a copy of your data, and try closing the books for a month end and see what happens to those accounts before you get too deep into GNUCash. Also, if you require cheque printing, you may want to test out that functionality before deciding to go ahead.

---

