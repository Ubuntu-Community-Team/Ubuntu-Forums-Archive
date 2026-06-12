---
title: "is there a (linux) equivalent to mailmaint (windows)?"
date: 2011-06-15
forum: General Help
---

### Post by dragonfly41 on 2011-06-15
For some time I've used **[COLOR=Navy]mailmaint[/COLOR]** in windows environment to filter out inbound mail from pop server before mail comes into the email client.  
Mailmaint is useful for clearing out junk mail.

> 
[http://www.magsys.co.uk](http://www.magsys.co.uk)

MailMaint is a POP3 Mailbox Maintenance application that supports multiple 
POP3 mailboxes, allowing headers to be accessed, and messages to be read 
and deleted. Old headers are stored on the PC, but this application is not
designed as an offline mail reader.  It's main purpose is deleting messages that 
have become stuck in the POP3 mailbox and are not being properly deleted by 
your normal email application.  This typically happens when the mail headers 
are corrupted or deliberately wrong (not uncommon with spam email).
Is there a ubuntu equivalent to act as a front end for Thunderbird email client?

Meanwhile I've installed mailmaint in wine.

The only problem is the small fonts seen in the GUI running in wine.   Otherwise it works.

---

### Post by ajgreeny on 2011-06-15
Pop3browser will do this for you, but it's a command line application;  very easy to setup and use, however, so don't be put off just because it is command line.

You might also look at mailwasher used in wine.  It does work, but not as simply as pop3browser.

---

### Post by dragonfly41 on 2011-06-15
thanks .. pop3browser seems to fit the bill ..

[http://manpages.ubuntu.com/manpages/gutsy/man1/pop3browser.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/pop3browser.1.html)

---

