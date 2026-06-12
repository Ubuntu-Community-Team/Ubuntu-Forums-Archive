---
title: "GnuCash Â Currency Problem"
date: 2006-05-09
forum: General Help
---

### Post by jonnymccullagh on 2006-05-09
I think this problem might be related to regional settings but any insight is appreciated.
I have set up GnuCash under Kubuntu and set currency as GBP i.e. £ - it has taken 2 nights to add in all my incomings and outgoings but now my invoices rather than displaying £ instead display Â£
I checked Gnucash website but this doesn't seem to be a problem elsewhere so I am guessing that it might be a "running Gnome app on Kubunutu" issue or some encoding issue maybe?
Has anyone any insight to this?
I could probably live with it but it is not very professional,

p.s. GnuCash usability 2 out of 10 so if anyone knows of something better for a very small business/personal finance - that might help,
thanks again,
jonny

---

### Post by vrih on 2006-05-11
I think gnucash doesn't like UTF-8 locales. You might be able to fix it by changing to en_GB.ISO-8859-15

For usability kmymoney might be a better bet. It doesn't have quite as many features as gnucash but it is quite simple.

---

### Post by jonnymccullagh on 2006-05-12
Thanks for the reply,
Can you tell me where I change the locale - is it within GnuCash or is it a system setting?

In relation to finance software, I agree - I hate GnuCash as it is a bit buggy and extremely user unfriendly - I would prefer a KDE program but KMyMoney does not allow me to create/manage invoices that I can see.
If I was a programmer I would help but my experience is in web development  so maybe I should create a web-based finance package myself. Alternatively I have seen Kumula which looks promising for the future and hopefully will have a finance module.
cheers,
jonny

---

### Post by JeffreyRatcliffe on 2006-06-18
Check out [https://wiki.ubuntu.com/GnuCashHowTo](https://wiki.ubuntu.com/GnuCashHowTo) for using gnucash with UTF-8.

Alternatively, install Gnucash 1.9.7 from Debian Sid. This supports UTF-8 natively.

Jeff

---

### Post by Al3xanR0 on 2006-07-06
[QUOTE=jonnymccullagh]I think this problem might be related to regional settings but any insight is appreciated.
I have set up GnuCash under Kubuntu and set currency as GBP i.e. £ - it has taken 2 nights to add in all my incomings and outgoings but now my invoices rather than displaying £ instead display Â£
I checked Gnucash website but this doesn't seem to be a problem elsewhere so I am guessing that it might be a "running Gnome app on Kubunutu" issue or some encoding issue maybe?
Has anyone any insight to this?
I could probably live with it but it is not very professional,

p.s. GnuCash usability 2 out of 10 so if anyone knows of something better for a very small business/personal finance - that might help,
thanks again,
jonny[/QUOTE]


Have you tried [Grisbi]("http://www.grisbi.org/screenshots.en.html")?

---

