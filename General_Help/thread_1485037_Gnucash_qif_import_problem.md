---
title: "Gnucash qif import problem"
date: 2010-05-16
forum: General Help
---

### Post by 73ckn797 on 2010-05-16
Running 10.04 64bit. Installed the latest Gnucash from repositories. Using Quicken 2003 and exported an account to a qif file. When trying to import to Gnucash the error "A bug was detected while reading the QIF file." displays. This, at least is more than I was able to do previously (prior to 10.04 and several earlier versions of Gnucash running in 8.04 through 9.10). Before it would cause Gnucash to crash and shutdown. I select a specific account with categories from Quicken to export. 

Any suggestions? I can import to KMymoney and use it but that program is not compatible with the wife and does not do reconciliation reports by default.

---

### Post by 73ckn797 on 2010-05-18
Bump

---

### Post by 73ckn797 on 2010-06-09
Nevermind! Guess no one has an answer.

---

### Post by 73ckn797 on 2010-11-25
Still no help.

Installed KMyMoney and the latest has reconcile function. It also imports qif flawlessly.

---

### Post by frankl6910 on 2011-12-08
> **73ckn797 said:**
> Running 10.04 64bit. Installed the latest Gnucash from repositories. Using Quicken 2003 and exported an account to a qif file. When trying to import to Gnucash the error "A bug was detected while reading the QIF file." displays. This, at least is more than I was able to do previously (prior to 10.04 and several earlier versions of Gnucash running in 8.04 through 9.10). Before it would cause Gnucash to crash and shutdown. I select a specific account with categories from Quicken to export. 

Any suggestions? I can import to KMymoney and use it but that program is not compatible with the wife and does not do reconciliation reports by default.
Had the same problem. Had to edit the qif file. Believe the was a space in one of the date fields. Not 100% sure it was the date, but if you're still interested, let me know, and I'll research which field it was.
Frank  L

---

### Post by 73ckn797 on 2011-12-08
I eventually found a category format was causing the problem. Edited that and it worked.

---

