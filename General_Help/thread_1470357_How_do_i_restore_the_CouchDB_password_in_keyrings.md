---
title: "How do i restore the CouchDB password in keyrings?"
date: 2010-05-02
forum: General Help
---

### Post by mixim on 2010-05-02
Hello, already beginning to destroy my new 10.04 installation :/ was conducting some diagnostics on the computer and removed passwords amongst keyrings that i thought was unused.

I deleted two CouchDB passwords, because i don't use Ubuntu One... But now i get an anoying warningmessage everytime I go into contacts in Evolution saying:

> **Error loading address book.**

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Address Book does not exist

How do I restore these passwords that seem to be needed for the adressbook to work properly, or how do I remove CouchDB Ubuntu One synchronization all together from Evolution.

// Regards, Joakim from Sweden

---

### Post by mixim on 2010-05-03
Solved this one by removing the config files for couch db...

 rm ~/.config/desktop-couch/desktop-couchdb.ini

then going in to synaptic package manager and completly removing " evolution-couchdb" then reinstalling it.

Don't know what of these did the trick but now i got my two keyring entries back and evolution doesn't complain when going into contacts!

Regards, Joakim

---

### Post by mixim on 2010-05-03
Deleted message

---

