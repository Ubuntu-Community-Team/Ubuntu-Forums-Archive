---
title: "error loading drupal"
date: 2009-09-20
forum: General Help
---

### Post by seuzo on 2009-09-20
Hi,

i got this error after install xampp and start xampp.

create a folder in home folder and link to /opt/lampp/htdocs/

when access [http://localhost/username/drupal-6.14/install.php](http://localhost/username/drupal-6.14/install.php)


Deprecated: Function ereg() is deprecated in /home/aik/public_html/drupal-6.14/includes/file.inc on line 902

Warning: Cannot modify header information - headers already sent by (output started at /home/aik/public_html/drupal-6.14/includes/file.inc:902) in /home/aik/public_html/drupal-6.14/includes/install.inc on line 618

Warning: Cannot modify header information - headers already sent by (output started at /home/aik/public_html/drupal-6.14/includes/file.inc:902) in /home/aik/public_html/drupal-6.14/includes/install.inc on line 619


anyone can advise on this?
i am lost
cannot reach the drupal/install.php

---

### Post by pcjunkie on 2009-09-20
ereg is php4 and php5 does not use it AFAIK, you might need to load the php4 module though I thought xampp already had done that.

---

### Post by seuzo on 2009-09-20
> **pcjunkie said:**
> ereg is php4 and php5 does not use it AFAIK, you might need to load the php4 module though I thought xampp already had done that.


i not sure also... how?

---

### Post by seuzo on 2009-09-21
the error is due to OS ubuntu problem or XAMPP?

---

### Post by pcjunkie on 2009-09-23
what does 

```
<?
	phpinfo();
?>
```

tell you?

---

### Post by thelevogyre on 2009-09-27
I am getting the same error. I have installed XAMPP1.7.2 and Drupall 6.14 in my Ubuntu Jaunty and I am getting this error:

**Deprecated**:  Function ereg() is deprecated in **/path/includes/file.inc** on line **902**

I have not touched any files. 

Help would be much apressiated...

---

### Post by solitaire on 2009-10-01
getting same error with xampp as well.

For some reason the lampp server i've also just installed (only 1 running at a time) cant see the SQL database properly...

Personally not a big issue! as i'll be wiping and installing Karmic in a week or 2..

---

### Post by tomthumb99 on 2010-01-01
Folks,

I am getting this on the drupal6 install, working througt the config menu:

Warning: fopen(./sites/default/default.settings.php) [function.fopen]: failed to open stream: No such file or directory in /var/www/drupal/includes/install.inc on line 188

Warning: Cannot modify header information - headers already sent by (output started at /var/www/drupal/includes/install.inc:188) in /var/www/drupal/includes/install.inc on line 618

Warning: Cannot modify header information - headers already sent by (output started at /var/www/drupal/includes/install.inc:188) in /var/www/drupal/includes/install.inc on line 619

Cannot get past Drupal config menu

Ubuntu ver 9.04
Drual 6

---

