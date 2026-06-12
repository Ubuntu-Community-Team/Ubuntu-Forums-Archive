---
title: "OpenOffice 2.0 OpenClipart?"
date: 2006-04-27
forum: General Help
---

### Post by matthias_k on 2006-04-27
Hi,

I'm running OO.org 2.0 on my Breezy notebook, and I want to install the openclipart-openoffice.org package, however, it depends on OO 1.1.

How can I install the clipart package for the new version of OO?

---

### Post by MartinG on 2006-04-27
The Automatix script to install OOo2 to Breezy also installs the OpenClipart.  You could inspect the script to see what it does and then run the relevant commands in a terminal (sorry I can't be more explicit, I've wiped Automatix after upgrading to Dapper).

---

### Post by matthias_k on 2006-04-27
[QUOTE=MartinG]The Automatix script to install OOo2 to Breezy also installs the OpenClipart.  You could inspect the script to see what it does and then run the relevant commands in a terminal (sorry I can't be more explicit, I've wiped Automatix after upgrading to Dapper).[/QUOTE]
Thanks, I just used the script to install the cliparts package, but it doesn't seem to show up in OpenOffice. The Gallery is completely empty!

Ideas?

---

### Post by MartinG on 2006-04-27
It may just be that the import has gone wrong.  Try creating a Gallery entry manually, then close OOo and re-open it, and see if your new entry is still there.  If it is, you can then add the OpenClipart stuff by hand -- tedious but not impossible.

If however you "lose" your new entry, then you may have the problem I had in Breezy, using the ubuntu packages of OOo2, when this happened to me (plus problems with Base).  My solution was to use the semi-official packages, from:
[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/)
These install in /opt rather than /usr, and of course updating is not picked up by the ubuntu updater, but they work well.

An alternative is to move to Dapper, which has a properly working version of OOo, and can install OpenClipart from Synaptic.

---

### Post by matthias_k on 2006-04-27
I'll definitely move to Dapper sooner or later, but right now I need my notebook to work with it, I don't want to take the risk to update to a beta right now. I need  a reliable productive system.

---

### Post by MartinG on 2006-04-27
One possibility is to manually download Dapper's OOo debs ([http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/)](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/)) and then install them with dpkg.  AFAIK Dapper keeps the files in the same place as Breezy, so you *should *get a clean upgrade.  It's a bit of an unknown, so whether you do it depends on how desperate you are ;)

---

