---
title: "PHP.ini"
date: 2011-03-09
forum: General Help
---

### Post by a.kleiner on 2011-03-09
[COLOR=#000000][FONT=Times New Roman][FONT=arial]My colleague and I are trying to set up Zen Cart on a box running Ubuntu 10.04. We're running into the following error when we attempt to go to the installation screen:

ERROR: date.timezone not set in php.ini. Please contact your hosting company to set the timezone in the server PHP configuration before continuing.

How would we fix this?
[/FONT][/FONT][/COLOR]

---

### Post by wiggly81 on 2011-03-09
my php.ini is located in /etc/php5/apache2 to edit this i would use somthing like
```
gksudo gedit /etc/php5/apache2/php.ini
```
search the file for date.timezone, mine is unset so i don't know what it should read and i don't use zen either

---

### Post by wojox on 2011-03-09
You can fix it by going to zc_install/includes/application_top.php and add following line on the top:

ini_set('date.timezone', 'America/Chicago');

Or what ever timezone you use. Then restart the server.

---

### Post by a.kleiner on 2011-03-09
Thanks guys! We were able to use your replies to solve the issue. Here's what we did:

[LIST]
[*]Used Ctrl+F to find the timezone property.
[*]Uncommented the line.
[*]Set the value to -6.
[/LIST]

---

