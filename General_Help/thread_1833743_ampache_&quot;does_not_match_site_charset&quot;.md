---
title: "ampache &quot;does not match site charset&quot;"
date: 2011-08-26
forum: General Help
---

### Post by thebrandon on 2011-08-26
So I installed ampache on my ubuntu server and I am trying to add my music files too it but I keep getting the error message "does not match site charset".  As far as I can tell everything is using utf-8, I know ampache's database entry in phpmyadmin all the collation is set to utf8_unicode_ci.  I turned logging on and the log file says "2011-08-26 13:32:56 [brandon] (PHP Error) -> [Runtime Error] htmlentities(): charset `s the default refresh limit in seconds for' not supported, assuming iso-8859-1 in file /usr/share/ampache/www/lib/general.lib.php(221)"  What can I do about this?  What am I missing?

---

