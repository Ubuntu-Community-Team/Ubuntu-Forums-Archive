---
title: "IMAP proxy-like server."
date: 2010-01-19
forum: General Help
---

### Post by chuckmoney on 2010-01-19
I have a POP3 server from my company's mail host that only keeps email for one year.  They offer no IMAP, no SSL, and refuse to send me backups in any format (except maybe an outlook PST file for a reasonable fee of $235/hour, of course.)  I also have a laptop running Ubuntu Server 9.04 on a static IP that I use as a personal web dev server.

My goal is this:  I want to set my email account on the web host, as well as my GMail account and possibly others to forward mail to IMAP running on my personal server.  My problem is I have no clue where to start to do this.  I know I will need to setup an IMAP server and I am considering dovecot for this.  However, the IP isn't a domain, just a static IP, so my first question is if I can forward to it without buying a domain?  Next, is there any chance I can use the system user account(s) for auth instead of yet another separate password DB?  Finally, if I can get this working at all, is there any chance that I can setup each account that's being forwarded to my personal server to go into a separate IMAP folder automatically?

I also hope when this is done I will be able to access the mail on 2 different laptops (my main and also an ASUS EEE).  This is another reason I want to do this so that half my GMail doesn't end up on one system and half on another.

So...what do I do?

---

