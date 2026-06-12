---
title: "utf 8 error with rssdent.php/simplepie"
date: 2009-09-06
forum: General Help
---

### Post by pete on 2009-09-06
I've spent the better part of the last two days trying to get rssdent ([http://github.com/zcopley/rssdent/tree/master]("http://github.com/zcopley/rssdent/tree/master")) working for feeding and RSS feed to a Laconica install.

I've got PHP5, simplepie, and all the various PHP5 xml libraries installed, but every time I run the script, it errors out with the following message:

[INDENT]Fatal error: Call to undefined function idn_to_utf8() in /usr/share/php/simplepie/simplepie.inc on line 7584[/INDENT]

All the googling I've done says this error means I don't have php xml support installed, but so far as I can tell, that is not the case.

Anyone have any ideas?

---

### Post by ug57amf on 2010-05-05
There seeme to be no answers to this, phpxml in most cases is not missing the php5-intl is missing and this is the problem: this can be resolved by entering the following at the command line:

 sudo apt-get install php5-intl

SimplePie then works!

---

