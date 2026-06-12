---
title: "Openoffice"
date: 2010-03-08
forum: General Help
---

### Post by Chamillionaire2 on 2010-03-08
What's Up?

OK, So whenever I need to read or write a text file, I'd always use text editor, And therefore and no need for the big and bulky open office, But now that I've un-installed it, It keeps popping up in update manager.

Is their anyway to stop receiving updates for it?

Thanks Bye!

---

### Post by 0nullun0 on 2010-03-08
sudo apt-get autoremove --purge
sudo updatedb

You could also go into update-manager, look for the openoffice entry, select it for 'complete removal', and 'click 'Apply'. 

Hope this helps.

0nullun0
m

---

### Post by Techsnap on 2010-03-08
Make sure you've uninstalled the whole thing, do a search for it in synaptic and remove any third party PPA you have added for OpenOffice.

---

### Post by Chamillionaire2 on 2010-03-10
Thanks I uninstalled everything to do with open-office, I did have a couple of packages that were still knocking about.

---

