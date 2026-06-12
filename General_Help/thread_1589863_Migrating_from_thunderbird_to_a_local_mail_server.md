---
title: "Migrating from thunderbird to a local mail server"
date: 2010-10-07
forum: General Help
---

### Post by motumboe on 2010-10-07
I have successfully installed and configured an imap mail server on a local network. The local imap mail server fetches mails from the remote mail server via POP3 and make them available to the local PCs via imap.

Previously we used thunderbird and we directly fetched mail from the remote mail server. Now we would like to have all the old thunderbird mails (we have them on our local pcs) made available on the local imap mail server.

So I have to copy the files containing mails in a local pc to the imap mail server. The imap mail server uses the Maildir format.
I suppose I have to make a format conversion...
Any suggestions? Thank you in advance.

---

### Post by HermanAB on 2010-10-07
Howdy,

Run Thunderbird, create a new IMAP account on the new server.  Highlight the email in the old account and click-drag-drop it to the new account.

That will work if and only if the new account is IMAP.

---

### Post by motumboe on 2010-10-07
It works!!!
Thank you very much Herman!!! :-)

---

