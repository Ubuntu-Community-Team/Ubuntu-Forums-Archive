---
title: "Certain sites redirecting to weird google searches"
date: 2009-07-02
forum: General Help
---

### Post by ManiacDan on 2009-07-02
Ok, here's a weird one for you guys. Certain websites that I visit every day have started resolving to a google search for the letter "P". I visit some of the gawker websites, like lifehacker and the consumerist. Recently, the consumerist started going here:
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&q=p](http://www.google.com/search?ie=UTF-8&oe=UTF-8&q=p)

I figured that it was just a problem with firefox, and I didn't have time to fix it. So I started visiting the site in Epiphany. Today, the same thing happened again, only this time BOTH gawker sites returned the google search for "P".

Oddly, when I type in the fully qualified URL ([http://www.consumerist.com](http://www.consumerist.com)) I get taken to [http://www.p.com](http://www.p.com).

Something is changing my sites to P, and I can't figure out what it could be.

OS: Ubuntu 9.04
Browser: Firefox, midbrowser, epiphany
Contents of my /etc/hosts are fine
The problem crops up after a couple months' use, and appears to be permanent in whatever browser is affected. NEW browsers will work fine, I installed opera this morning and that can still get to my sites. I hate to call that a "solution" though because I'll eventually run out of browsers.  Uninstalling and reinstalling doesn't help.

-Dan

---

### Post by ManiacDan on 2009-07-02
I seem to have fixed this by removing places.sqlite and places.sqlite-journal from the configuration directory of firefox and midbrowser.  I still don't know why it's broken in epiphany (though it's probably a similar thing).  

If someone runs across something like this, note that you have to back up your bookmarks before clearing your sqlite files in either of these browsers.

-Dan

---

