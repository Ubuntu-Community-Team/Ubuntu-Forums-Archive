---
title: "Firefox 3.6 unable to send link"
date: 2010-02-08
forum: General Help
---

### Post by rrwo on 2010-02-08
I'm using Firefox 3.6 on Jaunty, and now Karmic. Since upgrading Firefox from 3.5, I get this error when sending a link.

When I "Send Link", Firefox opens a Thunderbird compose window. But when I sent the e-mail, I get an error alert that says:

"Could not initialise the browser's security component. The most likely cause is problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard disc is not full or close to full. It is recommended that you exit the browser and fix the problem.  If you continue to use this browser session, you might see incorrect browser behaviour when accessing security features."

When I press Ok, I get another alert message:

"Thunderbird can't connect securely to [mail server] because the SSL protocol has been disabled."

Then I get a third alert message about being unable to connect to SMTP server.

I only get these errors when sending links from Firefox, if Thunderbird is not already open. Thunderbird works fine otherwise.

Hard drive space is no problem.  I also checked file permissions. I suspect the problem is related to app_armor, since the upgrade originally produced app_armor errors.  I tried reinstalling Firefox, but it has not fixed the problem.

---

