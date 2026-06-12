---
title: "[Citadel] Question regarding the SA &amp; ClamAV linking/plugins"
date: 2011-07-20
forum: General Help
---

### Post by blenderfox on 2011-07-20
I've setup Citadel and got it working with a few test users. I've also setup SpamAssassin and ClamAV according to standard settings and set them to listen to the relevant ports, and confirmed they are listening on those ports.

I've tied in Citadel to point to 127.0.0.1 for both SA and ClamAV, and used the Remote Retrieval to pull a test email from the remote server (for this test, I'm using POP3 to pull and email rather than have it pushed to my machine via SMTP). The email comes through successfully, but I see no SpamAssassin headers (score, rule matches, etc.) or any indication that ClamAV has scanned the email.

Question I have now, is have I setup the links correctly and/or is there a Citadel log I can check (I didn't find anything obvious in /var/log)?

---

