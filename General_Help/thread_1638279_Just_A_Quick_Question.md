---
title: "Just A Quick Question"
date: 2010-12-05
forum: General Help
---

### Post by LinuxCharms on 2010-12-05
I'm going to be installing Ubuntu on this lady's Windows computer.
She uses a Windows program called QuickBooks to do her organizing and stuff for her job. 


My question comes in where when I install Linux for her, will I easily be able to get QuickBooks back for her?

---

### Post by squishjt on 2010-12-05
Not sure If quickbooks itself could work under wine. If not you could try this [http://kmymoney2.sourceforge.net/index-home.html](http://kmymoney2.sourceforge.net/index-home.html).

Good luck.

---

### Post by LinuxCharms on 2010-12-05
Thanks mate, I'll get to work with this.

---

### Post by sikander3786 on 2010-12-05
I think it is a Windows specific program. Can you please provide a link to that?

I suspect you'll need to find a Linux alternative for that software or you can also try to run it in Wine (it might succeed and might not, no guarantees with Wine).

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Or may be run Windows inside Virtualbox (success rate would be much better, in fact 99.99%).

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

I would suggest to give her a try with Ubuntu Live CD. Let her try it. Test all the hardware and also you can install Wine in the Live CD environment and test your software with that ;-)

---

### Post by Verbeck on 2010-12-05
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=120](http://appdb.winehq.org/objectManager.php?sClass=application&iId=120)

looks like only some versions runs smoothly

---

### Post by smeggs on 2010-12-05
SQL Ledger is supposed to be pretty close to QuickBooks. 

Try it - [http://www.sql-ledger.org/](http://www.sql-ledger.org/)

Also, you may be able to get quicken or QuickBooks to work under wine. 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=120](http://appdb.winehq.org/objectManager.php?sClass=application&iId=120)


Sorry for the repeating info, these replies must have come in quickly, they weren't there when I posted. Sorry to echo everyone else. :P

---

### Post by Paul41 on 2010-12-06
My experience is that QuickBooks doesn't work in WINE. GNUCash is a Linux option also - [http://www.gnucash.org/](http://www.gnucash.org/)

---

### Post by deibu76 on 2010-12-12
I'm an accountant at a CPA firm, so I deal with MANY clients who use Quickbooks - it is the overwhemling standard and the most commonly-used accounting software for small businesses, whether its the owner taking care of their own books, or hiring a bookkeeper that can print checks, generate payroll easily and reconcile accounts.

Like many CPAs, I'm not a fan of Quickbooks' methods of accounting...  I could go into that!  :lol:

But, there isn't a substitute for Quickbooks, and GNUCash is no practical alternative.  I do *NOT* recommend trying to run Quickbooks under Wine either.  I ran Quickbooks 2006 under Wine successfully until it crashed, corrupting my company data - fortunately I had a backup from the prior month so that was all I lost.

Now I have a WinXP Virtualbox setup - I use it to run Peachtree Accounting, Quickbooks and all my tax software, and it works fine.  I'd recommend that for Quickbooks.

---

