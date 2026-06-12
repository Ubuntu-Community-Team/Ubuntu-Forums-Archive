---
title: "SugarCRM file permissions and display problems"
date: 2012-05-27
forum: General Help
---

### Post by afrodeity on 2012-05-27
SugarCRM css is garbled, something to do with the file permissions. I have done this according to the link [here]("http://support.sugarcrm.com/index.php?title=04_Find_Answers/02KB/02Administration/100Install/Required_File_System_Permissions_on_Linux&action=print")

```

cd /var/www/html/sugar
$ chmod 664 config.php
$ chmod -R 775 cache custom data modules

```

But no luck. Any idea what am I doing wrong?

---

### Post by maverickaddicted on 2012-05-29
May be you have to check the ownership of that folder
```

sudo chown –Rf apacheuser:apachegroup and folder name like….
sudo chown –Rf www-data:www-data sugarcrm
Give Write permitions for apache on some of SugarCRM Files
cd /var/www/sugarcrm
sudo chmod 766 config.php
sudo chmod 766 custom
sudo chmod -R 766 data
sudo chmod -R 766 cache
sudo chmod -R 766 modules

```

Here is the [SOURCE]("http://www.linuxgurru.com/2010/04/how-to-install-sugarcrm-on-ubuntu/")

---

### Post by afrodeity on 2012-06-02
thanks, that did the trick :)

---

