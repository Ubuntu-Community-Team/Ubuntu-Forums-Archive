---
title: "/etc/apache2/apache2.conf: Permission denied"
date: 2011-09-16
forum: General Help
---

### Post by bcbrown on 2011-09-16
I receive the following error when attempting to include a line in /etc/apache2/apache2.conf:
bash: /etc/apache2/apache2.conf: Permission denied

I am using the following command:
sudo cat >> /etc/apache2/apache2.conf

---

### Post by Dangertux on 2011-09-16
There is a policy about this, but this will not work with just sudo unless you chattr your apache2.conf (not a good idea)

you're going to have to do 

```

sudo bash

```

Then retry your command you will find it should work now.

---

