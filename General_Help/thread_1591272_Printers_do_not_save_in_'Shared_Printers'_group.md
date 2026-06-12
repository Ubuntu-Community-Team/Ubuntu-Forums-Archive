---
title: "Printers do not save in 'Shared Printers' group"
date: 2010-10-09
forum: General Help
---

### Post by nmyrick on 2010-10-09
I am having an issue that I hope someone can help me with.  I have a shared printer on my Ubuntu 10.04 machine, and it cannot be seen by other computers (macbook, pc) on the network.  I have the printer shared, but it is not a member of the 'Shared Printers' group.  When I add it to the 'Shared Printers' group, it stays there until I close the 'Printing' application GUI.  Then, when I re-open 'Printing,' it is no longer in that group. I think this is why I can't see it on the network, due to the wording of the option in Server Settings to 'Publish shared printers connected to this system.'

Can anyone help me with this issue?

---

### Post by nmyrick on 2010-10-14
Bump

---

### Post by pricetech on 2010-10-14
I'm going to ask since you don't mention it;  Do you have Samba installed ???

---

### Post by nmyrick on 2010-10-17
Yes, I have Samba  installed.  I have actually fixed this issue by _*removing*_ the printer from the Samba shares.  The Windows PC now prints fine, although it has a message under the installed printer in Windows that says 'access denied, could not connect to printer.'

---

