---
title: "Covering a few topics--Wine, LTSP, Thin Clients"
date: 2009-08-12
forum: General Help
---

### Post by Jago6060 on 2009-08-12
Hi all.  I wasn't sure exactly where this fit so I defaulted to General Help.

What I want to do: Run a Thin Client Server with Wine installed so the thin clients can use Office2007 without having to install it on every machine.

-Is this possible?
-Will Wine run on a Thin Client Server and if so, can it serve programs to thin clients?

---

### Post by Jago6060 on 2009-08-14
~Bump~

---

### Post by Ngallendou on 2009-08-15
By now you know that:

a) M$ ensured that Office will never run via Wine. :(

b) M$ licenses their Office suite per user. :(

Have you checked out OpenOffice.org ? It can do about 90 percent of what M$ Office does -- with practice. :)

---

### Post by Jago6060 on 2009-08-17
> **Ngallendou said:**
> By now you know that:

a) M$ ensured that Office will never run via Wine. :(

b) M$ licenses their Office suite per user. :(

Have you checked out OpenOffice.org ? It can do about 90 percent of what M$ Office does -- with practice. :)


Yeah! I'm a big fan of OO, its what I use.  But I work for a small company so were trying to rig cost savings every way we can.  I do have Office 2007 working in wine.  So my thought was is Office2007 was only installed on the Server, its only one license, then thin clients could use it through the server.  So I guess my idea for the tree is kinda like this...

LTSP Server-->Running Wine
|                           -->Office 2007
|
--------------------Thin Clients

---

### Post by djsephiroth on 2009-10-06
> **Ngallendou said:**
> By now you know that:

a) M$ ensured that Office will never run via Wine. :(

Then how have I been running it on our LTSP server? :confused:

> 
b) M$ licenses their Office suite per user. :(

Have you checked out OpenOffice.org ? It can do about 90 percent of what M$ Office does -- with practice. :)
Thing is... we've tried that suite, and there was a lot of backlash. Right now we're having enough issues just getting everyone over to Google Docs. The unfortunate reality of most businesses right now is that they see the MS logo as a stamp of legitimacy. I have been told, and I quote, "we want to be able to tell the parents of our students that they're learning Microsoft, because that's what they know, and if we tell them we're teaching them Google or OpenOffice, they won't know what that is." Yes, I know, painful, but it's honestly something not worth arguing about at length. What *should be* and what *is* are two different things. Sometimes - and in fact, I think most of the time - we need to focus in the little victories and the baby steps toward a more open future. Switching over to thin clients alone has saved us a significant amount ($150 clients with dual-core x64 Atom 330s and 2GB DDR2 :D). Running everything off of a Linux server means we make better use of the hardware (Core i7 920, 1.2TB RAID6 + hot spare on an Areca card, 6GB DDR3 1333, dual Intel GBE, etc. = not bad for about $2500). I'm slowly moving our online storage from Win2k3 to FreeNAS, one dept. at a time. It all goes slowly, but it's easier to swallow than having the entire user experience switched out overnight. 

Users hate learning new things, as a general rule. It's particularly true here: we have some people who do not understand that Gmail pass != Windows pass != other apps' passes; or who cannot figure out how to access anything that doesn't have a desktop shortcut. We can yell at them all we want for not being inquisitive, but it gets nothing done. Swallowing our pride and accommodating the users does more for the cause than any pedantry can possibly accomplish.  

To be legal, you need to buy the per-user licenses. However, if you have, say, 150 users and only about 50 logged in at a time... perhaps only purchasing 50 licenses? IANAL, but it may be worth investigating. Best of luck. What you're trying to do can be done, but you'll really want to look into Crossover instead of Wine. Worth every penny for production systems, plus you're supporting free/open software in the process.

---

### Post by djsephiroth on 2009-10-06
[http://www.bootpolish.net/pageloader.pl?page=home_howto_installwineonltsp](http://www.bootpolish.net/pageloader.pl?page=home_howto_installwineonltsp)

---

