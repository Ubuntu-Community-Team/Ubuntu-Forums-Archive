---
title: "How To Enable IMAP push (Gmail) in Evolution 2.30 (Ubuntu 10.10)"
date: 2010-10-19
forum: General Help
---

### Post by Nick Rhodes on 2010-10-19
Evolution brings us better IMAP support, supporting the [IMAP IDLE]("http://en.wikipedia.org/wiki/IMAP_IDLE") feature which allows for realtime notifications - commonly known as push notifications.

If your email provider supports IMAP IDLE (for example Gmail does), then you can enable IDLE support with 2 simple steps, when either CREATING or EDITING your IMAP account in Evolution.

1. When setting the Receiving Email Server Type select **IMAP+** from the dropdown. This tells evolution that your IMAP account supports IDLE.

2. Due a bug (that is now fixed in 2.32) you need to goto the Receiving "Options" tab and check the "Use idle if the server supports it" option"

After these 2 steps, you should be able to test instant notification of new emails without having to Send/Receive (either manual or automated).

Cheers, Nick

---

### Post by Isis242 on 2010-11-23
I upgraded evolution then tried this but I'm still not getting mail pushed. Has anyone been able to make this work?

---

