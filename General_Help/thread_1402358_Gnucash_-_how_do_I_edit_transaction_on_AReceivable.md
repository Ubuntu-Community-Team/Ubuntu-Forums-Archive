---
title: "Gnucash - how do I edit transaction on A/Receivables?"
date: 2010-02-09
forum: General Help
---

### Post by itsols on 2010-02-09
Hello everyone!

I'm trying to take off with GnuCash and I've been trying to work on the basics.

Here's my question: I don't want to enter all the details of bills sine there's another program for that. So I thought it would be right to enter the sales summary in the accounts receivable account and post the corresponding entry for the Sales account. Based on this,

1. What does the TYPE mean (I/P) on the receivable account?
2. I let it have I and now I want to go back and edit those entries but I can't seem to do that. It appears to be locked. Any ideas?

Thank you in advance.

---

### Post by tschaboo on 2011-04-02
I'm having the same question/problem. Any information would be appreciated.

---

### Post by itsols on 2011-04-02
Hi tschaboo, I gave up using GnuCash. I really thought we can take it to the next level since I'm also a developer. Unfortunately, I spent too much time trying to 'start up' things and there was hardly any support from the community.

At the moment I'm reconsidering some options and maybe I'll come up with my own thing or even go for another open source package temporarily.

You can also try the IRC channels but it's a long wait, and I wonder if it's worth it.

---

### Post by tschaboo on 2011-04-02
Hello itsols,

thx for your reply. I'm using GnuCash for my private accounting already for years. It's far from perfect, but the best (open source) I found yet...

I wrote an email to the German mailing list and I hope to get an answer there. If I get some solution or hints, I will translate them and post them here anyway.

---

### Post by itsols on 2011-04-02
I agree that for personal work, it is probably the best. It's easy to work with, like having macros on a spreadsheet. But in my case it's for my business and still it can be used with some tweaks...

And I hope you get an answer so that we may benefit from it as well. Thanks for that!

---

### Post by vongerther on 2011-04-03
Transaction types mean:
I = Invoice
P = Payment

I have the same problem. For personal use I'd like to simply type transactions into the list. But it seems that it is necessary to use the masks from the menu for creating and editing invoices and bills. 

This is not convenient, so I decided for me to not use the Accounts payable / accounts receivable feature for personal use.

---

### Post by tschaboo on 2011-04-03
I got an answer on the German mailing list. Here's what to do, when you are stuck with 'I'-Entries: 

* gunzip the gnucash-file
* search for "<slot:value type="string">I</slot:value>"
* remove the I
* gzip the file again
* open this new file with gnucash -> the entries are unlocked!

---

### Post by itsols on 2011-04-03
tschaboo, Thanks for sharing this.

Going by the simplicity of the program, the steps to unlock are definitely not meant for an ordinary user.

Nevertheless, it was worth knowing :)

---

