---
title: "Postfix not deleting mail files correctly"
date: 2009-11-18
forum: General Help
---

### Post by cpressland on 2009-11-18
Hi there,

I've just managed to get a Mail Server running on my Ubuntu rig, it sends and receives e-mails just fine. I'm using Postfix and pretty much all the Apps recommended by canonical on their site.

Anyway, when I delete an e-mail in my Mail Client and it goes into the Deleted Items, then clear my deleted items the actual Mail Files can still be found in /Maildir/cur

Am I missing something obvious or does the system auto-delete after a fixed period of time?

Thanks guys

CPressland

---

### Post by dcstar on 2009-11-19
> **cpressland said:**
> 
I've just managed to get a Mail Server running on my Ubuntu rig, it sends and receives e-mails just fine. I'm using Postfix and pretty much all the Apps recommended by canonical on their site.

Anyway, when I delete an e-mail in my Mail Client and it goes into the Deleted Items, then clear my deleted items the actual Mail Files can still be found in /Maildir/cur


Postfix does not "delete" mail, it is a MTA which moves mail from one node to another. Whatever underlying mail system that Postfix sends the mail to does any deleting (via the mail client you use).

---

