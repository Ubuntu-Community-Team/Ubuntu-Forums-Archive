---
title: "Evolution fetching e-mails redundantly (old and new?)"
date: 2012-02-01
forum: General Help
---

### Post by AFD8766 on 2012-02-01
When manually send/receive, Evolution attempts to fetch ~10,250 messages, about 200 more than are in the Inbox.  I cancel.

I've tried rebuilding the folder.db file, per <dcstar>, January 16th, 2010 in this thread:
[http://ubuntuforums.org/showthread.php?t=1085838]("http://ubuntuforums.org/showthread.php?t=1085838")

I've moved messages out of both the Inbox and Sent, into folders at the same level of hierarchy.  Inbox, the mailbox file in /home/alex/.evolution/mail/local/, is ~ 700 MB, and Sent is 1.1 GB.

Suggestions, questions, please.  

My next idea: basically use the instructions at that thread as given in the initial post.  My version:
1. With Evolution open, switch to working offline.  
2. Quit Evolution, make a copy of the entire /.evolution/mail/local/ folder, then move it to the desktop.  
3. Start Evolution, let it re-create the standard folders.  
4. Then move back only the mailbox files.  

Should I do this!!??  Suggestions, warnings, questions please!

Note that I have two accounts, and only one of the two addresses has this problem. It's the one with "leave messages on server," in case that matters. Does this tell me anything??

---

### Post by AFD8766 on 2012-02-12
Evolution now fetching only the most recent e-mails.  The "solution" was brute force, and did not completely work.

I removed the four inbox files from /.evolution/mail/local and re-started Evolution.  Forcing it to fetch everything (10,000 e-mails).  I did this several times, as it would stop fetching after a few thousand, seemingly when it was downloading a big one.  Despite this, everything seems to have been retrieved.  

Unfortunately, read/unread status was lost.  All e-mails displayed as unread.  

For what it's worth, I subsequently made several subfolders for old e-mails, sent and rec'd, and removed them onto an external hard drive.  

suggestions, comments all welcome.  Especially:  what can I do to avoid this problem happening in the first place?  Is there any kind of log or de-bugging info I could share?

---

### Post by AFD8766 on 2012-05-11
Short summary and update follows.
Receiving via POP server, sending via SMTP.
Evolution 2.28.3 on Ubuntu 10.04 (moving to 12.04 in less than a month).

At first I tried moving only the folder.db file (in /home/alex/.evolution/mail/local/) onto the desktop, and tried to send/receive.  This didn't solve the problem: Evolution wants to fetch everything on the server, not just new messages.  

So I moved folder.db and the four inbox files (Inbox, Inbox.cmeta, Inbox.ibex.index, Inbox.ibex.index.data) to the desktop and let Evolution fetch all the messages on the server.  Had I let Evolution fetch everything on the server, with only the folder.db file removed to the desktop, I would see double of every message.  

On my 450 kiB/s wireless connection, the download would hang when it came to certain big messages.  I tried to find a faster connection at a friend's house, and found that the *wired* connection was slower, and yet didn't hang.   

All messages appear unread now.  

Could I have done this in a more expedient way?  Can I do something to prevent this issue in the future?  Do the Backup and Restore functions have any role to play in any of this maintenance or prevention?

By the way, issues with Evolution can be discussed on the evolution e-mail list:
[email]evolution-list@gnome.org[/email]
[http://mail.gnome.org/mailman/listinfo/evolution-list]("http://mail.gnome.org/mailman/listinfo/evolution-list")

---

