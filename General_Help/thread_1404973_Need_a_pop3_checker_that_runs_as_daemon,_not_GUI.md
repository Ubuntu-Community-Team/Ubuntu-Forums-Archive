---
title: "Need a pop3 checker that runs as daemon, not GUI"
date: 2010-02-12
forum: General Help
---

### Post by misterbk on 2010-02-12
Hi guys,

Looking for a POP3 checker that can run in the background, not through any GUI or desktop environment, and either send an email or run a script when it sees email come in to a pop3 account.

Here's my plan:  I have an always-on linux box at home.  I don't sit at the box and would never see a GUI notification, though it does run KDE.  Would like to get instant notification of new email on my phone, similar to the push-email you get with Blackberry service.  I can accomplish this by texting my phone the subject and From field of new email, or at least texting "New Mail" to my phone when new email comes in to a specific pop3 account.

Any ideas?  Google searches just lead me to those dumb fake-a-search pages that regurgitate my search terms back at me along with links to their sponsors.

---

### Post by misterbk on 2010-02-12
Actually, I thought about it for a sec, and realized I could get what I want with just an email forwarder.

In case anyone else comes across the thread and wanted something similar...  I gave up on google and started digging around in aptitude.  Found a little program called "fetchmail" that runs as a daemon.  The intended purpose was to retrieve email from a remote account and store it locally for easy access, the example use being someone who has dialup and wants the email waiting locally when they get home.

It seemed like fetchmail could be configured to do other things and could probably be used along with other scripts and utilities run on the local mailbox.  (To answer my original question, even though an email forward does it for me.)

---

