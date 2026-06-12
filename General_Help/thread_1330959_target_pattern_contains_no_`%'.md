---
title: "target pattern contains no `%'"
date: 2009-11-18
forum: General Help
---

### Post by sum1nil on 2009-11-18
Hi,
I'm trying to build a program from source. I get the error:
make[2]: Entering directory `/home/Dev/src/Working/conglomerate-0.9.1/po'
Makefile:190: *** target pattern contains no `%'.  Stop.

I'm not sure what it means or how to fix it. I'm not sure but I think the 'po' directory is for internationalising the programs languages.
The makefile line is:
POFILES =  az.po ca.po cs.po da.po de.po el.po en_CA.po en_GB.po es.po fr.po hr.po ja.po nl.po no.po pa.po pl.po pt.po pt_BR.po ru.po rw.po sq.po sr.po [email]sr@Latn.po[/email] sv.po uk.po zh_CN.po 

Thanks in advance for any help.
:popcorn:

---

### Post by BinaryFeast on 2009-11-18
Spontaneously: what happens if you delete " [EMAIL="sr@Latn.po"]sr@Latn.po[/EMAIL]" from the makefile? Not that I have any kind of experience with this kind of thing.

---

