---
title: "Mini Firefox Freeze when filling forms"
date: 2009-08-10
forum: General Help
---

### Post by nostra16 on 2009-08-10
Hi,

I've been running Ubuntu as a consumer now for over a year, and have been concerned lately because of mini freezes of Firefox.

This always occurs when I'm filling a form. Each time I type an e-mail address, the browser mini-freezes (no blacked screen, just no response). But I can keep on typing and the browser catches up quiet nice.

This concerns me. As a former Window$ user, this acting usually meant spyware, or keyboard catcher. In any case, it was a symptom of malware.

After some research I learned that there were very few viruses in Ubuntu, and even less anti-virus software. I know it's hard to get viruses and all, but my concern is that a harmware installed itself through Firefox Add-ons. I know I like to play around a lot with Add-ons, testing and trying.

Is this possible? How can I check? And how can I fight?

Thanks!

nostra16

---

### Post by lovinglinux on 2009-08-10
This is probably due to database junk. Firefox features that suggest words while you type look for matches on sqlite databases, which are slow. So if your database is full of junk, then it can take longer to perform actions that shouldn't be CPU intensive. 

Take a look at the Database Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). This should improve your experience considerably.

---

