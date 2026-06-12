---
title: "canot get cacti to work for anything"
date: 2006-06-12
forum: General Help
---

### Post by mrweirdo on 2006-06-12
I just recnetly installed catci from the apt sources aka
apt-get install cacti
well everything was ok except that hte graps dont display at all. So after some reading over at the cacti site i find out that I have to run poller.php in /usr/share/cacti/site
so I go to do this and then i get this nice error message:

Fatal error: Call to undefined function mysql_pconnect() in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 372

Does anyone have any ideas how I can fix this? I am completly lost at this point as both php5-mysql and php5-mysqli are installed.

---

### Post by mrweirdo on 2006-06-12
hrm dpkg-reconfigure php5-mysql fixed it. Not sure why it was messed up in the first place but now it works :)

---

### Post by jojonux on 2006-06-24
[QUOTE=mrweirdo]hrm dpkg-reconfigure php5-mysql fixed it. Not sure why it was messed up in the first place but now it works :)[/QUOTE]

Finally see some graphs.. Man u're my hero :D :D

---

