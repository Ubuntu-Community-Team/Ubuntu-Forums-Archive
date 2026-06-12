---
title: "exporting ALL evolution address books"
date: 2010-03-26
forum: General Help
---

### Post by rdh61 on 2010-03-26
Exporting the default evolution address book to a cvs file is relatively simple:

"There is an obscure utility called evolution-addressbook-export that does the job. To find it use the locate command on your system as it isn't in your normal path. Mine was located :

/usr/libexec/evolution/2.6/evolution-addressbook-export

to use is simple :

/usr/libexec/evolution/2.6/evolution-addressbook-export --format=csv >contacts.csv"

(From: [http://forums.fedoraforum.org/showthread.php?t=142680](http://forums.fedoraforum.org/showthread.php?t=142680)).

But this ONLY exports contacts from the default address book (Personal address book), not other address books one may have created in evolution. SO HOW SHOULD THE COMMAND BE MODIFIED TO EXPORT ADDITIONAL ADDRESS BOOKS THAT ONE HAS CREATED?

Cannot find an answer to this anywhere - most frustrating.

---

### Post by demarshall on 2010-12-18
Great utility but it doesn't reside in that directory in all recent versions of Ubuntu. I found it in usr/bin but just do a search for it on your computer and you'll find it.

---

### Post by absolutedesmond on 2011-03-06
You can use the -l option to look up the address book id
so:

evolution-addressbook-export -l

and then
evolution-addressbook-export --format=csv ID >contacts.csv

---

### Post by rdh61 on 2011-03-06
Thanks absolutedesmond. So, if "evolution-addressbook-export -l" gives me:

"file:///home/robert/.evolution/addressbook/local/1262372077.2151.31@robert-desktop","Ibz PP En",33

what, of this, do I use as the ID in the next command?

---

