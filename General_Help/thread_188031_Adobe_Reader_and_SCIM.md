---
title: "Adobe Reader and SCIM"
date: 2006-06-03
forum: General Help
---

### Post by bsun on 2006-06-03
I cannot use them at the same time. Only after I removed scim, I can use acroread.

---

### Post by magomago on 2006-06-03
yup...same problem existed in breezy

---

### Post by bsun on 2006-06-05
Problem solved. Just add this line in the script file acroread:
export GTK_IM_MODULE=xim

from here: 
[http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started](http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started)

---

