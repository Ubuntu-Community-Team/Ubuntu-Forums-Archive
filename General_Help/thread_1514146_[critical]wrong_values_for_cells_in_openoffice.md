---
title: "[critical]wrong values for cells in openoffice"
date: 2010-06-20
forum: General Help
---

### Post by JanMalte on 2010-06-20
I just discovered a very critical bug at the openoffice packages shipped with Ubuntu Lucid. I already posted an [launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/596231") but don't know if it is the right place for it.

Opening a file with protected table a simple cell has the wrong value. If i open the file with OOo from Jaunty or the version 3.2.1 from the OOo.org website it has the correct value. Even Kspread has the rightvalue for the cell. The file where we discovered the behavior is this one:
[http://www.kvjs.de/fileadmin/user_upload/fachoeffentlich/jugendhilfe/tagesbetreuung/formulare/Berechnung_Personalbedarf_1_0.xls](http://www.kvjs.de/fileadmin/user_upload/fachoeffentlich/jugendhilfe/tagesbetreuung/formulare/Berechnung_Personalbedarf_1_0.xls)

As this is a very basic function of OOo and Lucid is a LTS version this seems very critical for me.

A simple fix is using the version from OOo.org and install it instead of the ones from the repos. By doning this, i lose all the addons i installed from the repos.

So i would suggest to update or just fixing this bug, because this can be really bad if someone is doing buisness with OOo and getting wrong cost for something, just because OOo can't read the value from a single cell correctly.

---

