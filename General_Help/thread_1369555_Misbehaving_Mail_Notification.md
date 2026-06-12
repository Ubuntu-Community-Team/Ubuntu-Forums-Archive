---
title: "Misbehaving Mail Notification"
date: 2010-01-01
forum: General Help
---

### Post by keeblerelfmatt on 2010-01-01
I'm using Mail Notification 5.4. It worked just fine in Debian 5.0.3, but it appears to be misbehaving since I moved to Ubuntu 9.10, with an identical configuration.

I've set it up to check three mail accounts - two IMAP, and one Gmail. It behaves fine with the IMAP accounts, displaying up the mail notification in the popup stack. However, with Gmail it behaves differently - it pops up a dialog box. It didn't do this in Debian.

What can I do?

---

### Post by Gillingham on 2010-01-02
I have the same issue with notifications from my Gmail account.  

Anyway after some searching I found this bug in Launchpad [http://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/332767]("http://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/332767"), I found that the "horrible" work around that Dylan mentions in post #5 did work for me.

Sorry for taking a while I had to wait until I got new mail while actually at my computer :-)

---

