---
title: "Add Remove Applications Not working"
date: 2009-08-15
forum: General Help
---

### Post by ran1wil on 2009-08-15
When i open this nothing shows inside the message i get is: There is no matching application available. Please help i do not think my updates are working either.

---

### Post by michy99 on 2009-08-15
What error do you get if you try to start it from a terminal?```
gnome-app-install
```

---

### Post by ran1wil on 2009-08-15
** (gnome-app-install:8336): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1295: GtkWarning: gtk_tree_model_sort_set_sort_column_id: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_sort_column_id(-1, sort_type)

---

### Post by michy99 on 2009-08-15
Try this:```
sudo apt-get install --reinstall gnome-app-install
```

---

### Post by ran1wil on 2009-08-15
Thank you that worked great. I understand what just happened but could of never figured it out by myself thank you

---

### Post by michy99 on 2009-08-15
I have no idea how it got messed up, but I'm glad that reinstalling fixed it.

---

### Post by colau on 2009-08-16
> **ran1wil said:**
> Thank you that worked great. I understand what just happened but could of never figured it out by myself thank you
May be, missing some packages or something is broken.

---

