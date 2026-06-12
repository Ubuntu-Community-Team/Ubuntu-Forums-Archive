---
title: "Send email from script using exchange server credentials?"
date: 2010-03-23
forum: General Help
---

### Post by shawn.bordeaux on 2010-03-23
I want to create a shell script that generates a file and then sends it via email from my Ubuntu desktop by using my Exchange 2003 Server which is on a separate windows machine on my network.

I do not have an smtp server set-up so that is one of the reasons I want to go this route. The other is because I will be able to sync the emails sent from the exchange server.

Please let me know if this is able to be accomplished and how?

Thank you and best regards,

Shawn

---

### Post by dcstar on 2010-03-24
> **shawn.bordeaux said:**
> I want to create a shell script that generates a file and then sends it via email from my Ubuntu desktop by using my Exchange 2003 Server which is on a separate windows machine on my network.

I do not have an smtp server set-up so that is one of the reasons I want to go this route. The other is because I will be able to sync the emails sent from the exchange server.
........

Simply install the **mailx** and **postfix** packages and set up Postfix to use the Exchange Server as its "Satellite" - all outgoing emails using the **mail** command will then be routed through it.

---

