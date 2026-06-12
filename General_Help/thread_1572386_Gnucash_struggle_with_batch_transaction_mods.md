---
title: "Gnucash struggle with batch transaction mods"
date: 2010-09-11
forum: General Help
---

### Post by murphycc on 2010-09-11
In my search for personal financial software, I looked most closely at kmymoney, gnucash, ynab, and moneydance (to which I'm leaning).

But one thing about gnucash I found surprisingly difficult, and that was when I wanted to batch-change categories/accounts in a ledger for my imported credit card transactions.

Even after searching on the web I saw that there is no easy way to select, say, 10 transactions in my credit card account ledger and categorize them (really it's called assigning an 'account' since it's double-entry accounting). I would have to go through each one individually and assign it the same 'account'.

For those of you who use Gnucash, is this just a one-time inconvenience you dealt with when you imported your first 6 months' worth of credit card data and had to assign these 'categories'? If you import transactions consistently every month or so, do you just assign the categories one by one? It seems like a lot of time to not have the batch-change command.

I almost went with Kmymoney (v4.5) but there are a few things I do not like about it. I am most happy with MoneyDance, but I wanted to try to understand this issue with Gnucash one more time.

Thanks for any insight into this...
Chris

---

### Post by hokiejp on 2011-01-09
I am just going through this myself.  There is no way to select multiple transactions in GnuCash.  They do have code which tries to guess where imported transactions will go, however.

Go to Edit->Preferences->Online Banking and tic the "Use Bayesian Matching" box.

This will learn how you classify transactions during the import process (using the power of Bayesian statistics!) and classify future ones for you automatically.  What you can do is import the first 1-2 months of transactions and classify them manually in the import window.  Then try importing the next batch and hopefully it will guess most of them right.

---

