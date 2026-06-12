---
title: "OfflineIMAP and procmail?"
date: 2011-12-05
forum: General Help
---

### Post by MattBD on 2011-12-05
I'm in the process of reviewing my email setup. I was running my own mail server on a Pogoplug running Debian Squeeze, but this has proven to be fairly unreliable as I was running it off a flash drive and had to use ext2 rather than a more reliable filesystem, so I'm looking to move it to one of my laptops.

My previous setup consisted of Gmail, Postfix, Dovecot, fetchmail via POP, procmail, SpamAssassin and mutt. This worked pretty well, but fetchmail seemed to be decidedly slow using POP. I figure IMAP will be quicker, but fetchmail's IMAP support seems pretty poor - it only seems to sync either everything in the account, or everythinbg that's unread, so if I read something on my Android phone, for example, it won't get synced.

I'm therefore thinking I need to swap out fetchmail for something else. I'm not planning to run Postfix and Dovecot on a laptop, so I'm thinking mutt, procmail and SpamAssassin, with OfflineIMAP replacing fetchmail for downloading emails. However, despite some Google searches, I can't find much about using procmail with OfflineIMAP. I already have a solid procmailrc that does pretty much what I want, so I'm reluctant to ditch it for another filtering solution.

Has anyone used procmail with OfflineIMAP? How do I go about setting OfflineIMAP to work with procmail? Or can anyone point me in the direction of a tutorial that explains how to do it?

---

