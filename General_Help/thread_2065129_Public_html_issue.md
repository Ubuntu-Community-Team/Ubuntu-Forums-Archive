---
title: "Public_html issue"
date: 2012-10-01
forum: General Help
---

### Post by hhaydoura on 2012-10-01
I want to add a user and assign him a home directory, and a public_html.. i'm just wondering about the steps to complete this issue, can anyone help me doing this? thanks :)

---

### Post by Lars Noodén on 2012-10-01
You have to activate that module first.  But other than that the default settings should work.

```

sudo a2enmod userdir
sudo service apache2 restart

```

Then of course the directory public_html has to exist in the user's home directory.

---

### Post by Lars Noodén on 2012-10-01
The Apache configuration settings for the user directories will be here: /etc/apache2/mods-available/userdir.conf

---

### Post by hhaydoura on 2012-10-02
Thanks my ubuntu friend :) and am I supposed to put anything in the Apache configuration settings for the user directories ??

---

### Post by Lars Noodén on 2012-10-02
If it works, then you can leave /etc/apache2/mods-available/userdir.conf as it is.  But if you decide on changes later, that's where they'd go.

---

