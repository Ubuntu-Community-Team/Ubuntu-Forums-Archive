---
title: "why does my SSH key fail after reboot?"
date: 2012-06-23
forum: General Help
---

### Post by anon0 on 2012-06-23
this is what's been happening to me:

I reboot the machine.
I connect by SSH by my SSH private key, but it fails.

I go to the machine's physical location to log in.
I enable SSH authentication by password in /etc/ssh/sshd_config.

I remotely connect by SSH by user password, and it works.
I disable SSH authentication by password in /etc/ssh/sshd_config.
I connect by SSH by the same SSH private key as earlier, and now it works.

If I reboot, the cycle repeats.

Any idea?

Edit: I also noticed that SSH key works again as soon as I comment out "PasswordAuthentication no" and restarted the service, and it remains to work after I set it back to "PasswordAuthentication no".

---

