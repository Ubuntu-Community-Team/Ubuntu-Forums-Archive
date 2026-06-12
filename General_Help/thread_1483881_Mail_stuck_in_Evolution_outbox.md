---
title: "Mail stuck in Evolution outbox?"
date: 2010-05-15
forum: General Help
---

### Post by blueghoti on 2010-05-15
Hi all - 

Something very weird happening with email stuck in my outbox.  I am on Ubuntu 9.10 and Evolution 2.28.1

I have about 8 email boxes set up - all IMAP, all on different domains, and across several ISPs.  My primary ones have been working fine since I first set up Evolution about 3 weeks ago.

The less important ones had problems (I could receive but not send).  I've started to address these ones and am making relevant changes to SMTP server settings etc and they seem to working now.

However, one of my primary addresses seems to now be queueing email in the outbox and not actually sending it.  I did not consciously make any changes to that profile while I was fixing the other accounts.  I thought there might be an issue with my ISP, but having waited overnight to resolve any potential problems, I see I still have the same problem.

Couldn't seem to find any relevant guidance.  Anyone know what might be happening and how I can fix this?

Cheers, 
Chris

---

### Post by lisati on 2010-05-15
If Evolution encounters a problem sending, it often displays a warning message. If you don't get a popup with an error, check at the bottom of the Evolution window for an error warning in the form of a yellow triangle - clicking on the warning icon should bring up the popup.

---

### Post by blueghoti on 2010-05-15
Thanks lisati.  That helped diagnose.

I played around with some other settings and reverted to the old settings for one of my secondary accounts.  When I did this, I couldn't send from the other account, but it seemed to unblock sending for the ones I need to have access to now.

Thanks!
Chris

---

