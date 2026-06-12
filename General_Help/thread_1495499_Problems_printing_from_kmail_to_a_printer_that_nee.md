---
title: "Problems printing from kmail to a printer that needs user authentication"
date: 2010-05-28
forum: General Help
---

### Post by luispinho on 2010-05-28
Hi,

If I print to a normal printer kmail messages with or without attachments there's no problem printing, but if I try to print to a printer that needs authentication then I can only print some messages.

- Messages that contains attachments are not printed
- Messages without attachments are printed

I'm kubuntu 9.10 and my lpoptions file if like this:

#~/.cups/lpoptions
Default KM-420-2 _kde-filters=true KMAuthName3=HoldKey8 KMAuthName4=HoldKey9 KMAuthPass5=HoldKey1 KMAuthPass6=HoldKey9 KMAuthPass7=HoldKey6 KMAuthPass8=HoldKey2 KMBoxNumber8=StoreKey8 KMBoxNumber9=StoreKey9

The result found in /var/spool/cups for printed messages with attachments does not contain the authentication information found in lpoptions, while the other successful printings contains it.

Could anyone help me please ?

---

