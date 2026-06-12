---
title: "Some help for a newbie (Firefox issue)"
date: 2010-04-20
forum: General Help
---

### Post by 1devils1 on 2010-04-20
Been using windows for as long as I can remember. 

Just insalled Ubuntu 9.10 on a machine and really loving the speed.

Down to the issue I have..

Installed the Linky plugin for firefox.

Now Firefox loads up - then greys out - Then returns to correct colours, However nothing is clickable - Can't type anywhere etc.

After loads of reading managed to remove the contents of the plugins directory.

This did not solve the issue. 

With the 1st instance of firefox running I opened a 2nd instance. - The 2nd operates as expected while the 1st instance seems to have locked up.

Any idea's would be gratefully received.

Paul

---

### Post by VCoolio on 2010-04-20
Plugins are no extensions (add-ons). Find your installed add-on in ~/.mozilla/firefox/xxx.default/extensions, or remove it using the working second window. Or create a new profile (firefox -P nameofnewprofile) and see if that helps.

---

### Post by 1devils1 on 2010-04-20
Thanks VC.

It was a profile issue.

ran firefox -P 

Alls now okay

---

