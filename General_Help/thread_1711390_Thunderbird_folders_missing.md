---
title: "Thunderbird folders missing"
date: 2011-03-21
forum: General Help
---

### Post by serlex on 2011-03-21
Hi,

I'm running maverick with Thunderbird 3.1.9 and my 'All folders', left menu, are missing. Any suggestions to how I can restore these on a new install?

Regards,
Sercam

---

### Post by SeijiSensei on 2011-03-21
This depends a lot on what kind of mail system you use.  IMAP users often have all their mail stored on the server; POP users usually have local folders.

All your Thunderbird settings reside in $HOME/.thunderbird.  If during reinstallation you overwrote your home directory and didn't keep a backup, I'm afraid you might be out-of-luck.

If you do have a copy of your .thunderbird directory, just shut down Thunderbird, copy over the .thunderbird directory from backup, and restart Thunderbird.  Everything should be back the way it was.  

However if you already downloaded some mail from your account, you'll need to proceed more cautiously since overwriting .thunderbird will delete those messages.  You could forward any new messages to your mailbox and avoid downloading them again before switching over.

---

