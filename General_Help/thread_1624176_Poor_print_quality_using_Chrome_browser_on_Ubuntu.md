---
title: "Poor print quality using Chrome browser on Ubuntu"
date: 2010-11-17
forum: General Help
---

### Post by bkline on 2010-11-17
Anyone else experiencing ugly print quality using Chrome under Ubuntu?  I've got a Brother HL-5370DW.  Print output is beautiful with:
[LIST]
[*]Firefox 3.6.12 / Ubuntu 10.10
[*]IE 8.09.7600.16385 / Windows 7
[*]Chrome 7.0.517.41 / Windows 7
[/LIST]
With Chrome 8.0.552.200 beta / Ubuntu 10.10 the output is so bad that text is almost unreadable.

---

### Post by stevecoh1 on 2011-08-07
Yeah, I notice this too, except I'm using 10.04.  Printing in Chrome sucks on Ubuntu.  Hsve gotten no help on this either here or on Google Chrome website after months of putting up with it.  I am using the same printer as you are, by the way.

Did you ever get an answer?

I think there's enough here to write a bug report.

Are you using the standard Foomatic driver?

---

### Post by bkline on 2011-08-07
No, I haven't found a solution to the problem.  In fact, it's worse now, because now (Ubuntu 11.04) the print quality from Firefox is poor as well.  If I hook a Windows machine to the network and send output to the same printer (which is physically connected to the Ubuntu workstation) the output is much crisper.  Yes, I'm using the recommended foomatic driver.

---

### Post by stevecoh1 on 2011-08-07
I was just writing that bug for the Ubuntu system when I thought I should probably try again with the latest upgrade I'd just gotten from Ubuntu before sending it.  

Much to my surprise, the problem was gone.  Many previous upgrades had not solved the problem.  But this one did!  Google Chrome seems now to have a much better Print Preview integrated right into the Print command and best of all, it works right on the HL-5370DW.  That's Google Chrome version 13.0.782.107.

At least this is the case for Ubuntu 10.04.

---

### Post by maxar6 on 2011-08-07
Are you using chromium browser or google chrome? I have much better results when i use google chrome. Stupid question but did you just by the ink or is it almost empty. Those are the times when i have the most trouble.

---

### Post by bkline on 2011-08-08
> **stevecoh1 said:**
> Google Chrome seems now to have a much better Print Preview integrated right into the Print command and best of all, it works right on the HL-5370DW.  That's Google Chrome version 13.0.782.107

Thanks for the update.  I had removed Chrome and then later on noticed that Ubuntu was including "Chromium" in its own repositories, so I installed that, hoping the problem would be gone, with the help of official Ubuntu support (it wasn't).  But that doesn't have a version 13, so I suspect "Chrome" and "Chromium" are different browsers.  Does it really need to be this confusing? :-)

Time for some more investigation.

---

### Post by bkline on 2011-08-08
> **maxar6 said:**
> Are you using chromium browser or google chrome? I have much better results when i use google chrome. Stupid question but did you just by the ink or is it almost empty. Those are the times when i have the most trouble.

The cartridge has plenty of ink; that wasn't the problem.

As noted in my previous message, I'm just realizing there's a difference between "Chrome" and "Chromium" (why do they do this?).  I just added the google repository to my source list and installed Chrome (but it came in as version 7, not 13 as stevecoh1 reports).  Now the output print quality is spectacularly good!  Thanks for the tip!

---

### Post by bkline on 2011-08-08
I'll create a new thread for this (unless one already exists), but now that the Chrome print problems have been resolved, it would be nice to be able accomplish the same thing with Firefox, whose print output is as bad as Chrome's was when I first reported it.

---

