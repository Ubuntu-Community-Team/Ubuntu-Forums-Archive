---
title: "Could not find package during &quot;aptitude remove&quot;"
date: 2010-12-07
forum: General Help
---

### Post by vancouverite on 2010-12-07
Hello,
I'm trying to replace the ubuntu version of openoffice with the official release.  During this procedure I ran the command:
sudo aptitude remove openoffice.org-*

and get the error:
Couldn't find any package whose name or description matched "openoffice.org-ure_1.6.1-18_amd64.deb"

I went in to synaptic and removed all the openoffice packages through the GUI (none of which matched that name) as well as the UNO and URE packages.  Even after uninstalling all the packages, if I run the aptitude command again, I get the same error.

What is going on here?  Does it indicate that my package database has been corrupted?  Can I rebuild the database?  Should I just ignore this error?

Thanks for your help.

Van

---

### Post by vancouverite on 2010-12-07
Ah!  I figured it out! I was in the folder of debs downloaded from the openoffice website when I ran the command.  One of the debs matched that name, so it was trying to uninstall a package that was named in the folder.

Silly mistake.

Van

---

