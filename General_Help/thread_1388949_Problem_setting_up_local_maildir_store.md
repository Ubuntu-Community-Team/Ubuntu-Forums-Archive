---
title: "Problem setting up local maildir store"
date: 2010-01-23
forum: General Help
---

### Post by mikerobinson on 2010-01-23
I have set up postfix, dovecot and mailx on my computer. I can send e-mails via the command line to my local user just fine and connect fine via IMAP and retrieve them, however when I type mailx it always says I have no mail. I have a feeling it is looking for the default mbox store at /var/mail/$USER. How can I make it so that the "mailx" command looks for mail in my maildir store in ~/Maildir instead?

---

