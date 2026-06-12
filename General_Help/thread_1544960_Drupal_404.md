---
title: "Drupal 404"
date: 2010-08-03
forum: General Help
---

### Post by peredur on 2010-08-03
Hi all,

I've downloaded and extracted Drupal6 to my apache installation on Ubuntu 10.04, to the folder /var/www/drupal6; and I've changed the owner and group on that folder:

sudo chown -R www-data:www-data drupal6

I then try to open the Drupal installation application:

[http://localhost/drupal6](http://localhost/drupal6)

Apache replies with a 404 'The requested URL /drupal6 was not found'

I'm obviously missing something, but for the life of me I can't see what it is.  Could somebody please put me out of my misery?

Thanks


Peter
[http://www.peredur.net](http://www.peredur.net)

---

### Post by indytim on 2010-08-03
You need to change your ownership to
/var/www/drupal6

IndyTim / DataMan

---

### Post by sirnicolas21 on 2010-08-03
```
sudo chown -R g+r /www/var/drupal6
```

i think

---

### Post by indytim on 2010-08-03
No,

The typical LAMP is installed at /var/www

-IndyTim / DataMan

---

### Post by peredur on 2010-08-03
> **indytim said:**
> You need to change your ownership to
/var/www/drupal6

IndyTim / DataMan

Heh!  To what?  Currently the drupal root directory and all sub-directories have 755.  The files inside the drupal root (all in all sub-directories) have 644, except for /drupal6/sites/default/settings.php which has 666.  The ownership is www-data:www-data.

Cheers


Peter

---

### Post by peredur on 2010-08-03
> **sirnicolas21 said:**
> ```
sudo chown -R g+r /www/var/drupal6
```

i think

Nope.  Everything already has read permissions.

Cheers


Peter

---

### Post by peredur on 2010-08-03
> **indytim said:**
> No,

The typical LAMP is installed at /var/www

-IndyTim / DataMan

Oh!  Are you saying Drupal can't be installed into a sub-directory under the Web server root?  That would definitely put me off developing with Drupal.  Surely that can't be right??

Chees


Peter

---

### Post by sirnicolas21 on 2010-08-03
no he just noticed my mistake cause i flipped the /var/www into /www/var

---

### Post by peredur on 2010-08-03
> **sirnicolas21 said:**
> no he just noticed my mistake cause i flipped the /var/www into /www/var

Heh!  Better eyesight than I've got.

Cheers


Peter

---

### Post by peredur on 2010-08-03
> **peredur said:**
> Hi all,

<snip />

I then try to open the Drupal installation application:

[http://localhost/drupal6](http://localhost/drupal6)

Apache replies with a 404 'The requested URL /drupal6 was not found'

I'm obviously missing something, but for the life of me I can't see what it is.  Could somebody please put me out of my misery?




D'oh!

/etc/init.d/apache2 restart

Sorry for time wasting.


Peter

---

