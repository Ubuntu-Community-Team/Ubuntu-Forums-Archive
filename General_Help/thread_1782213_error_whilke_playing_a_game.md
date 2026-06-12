---
title: "error whilke playing a game"
date: 2011-06-14
forum: General Help
---

### Post by jagan605 on 2011-06-14
i get this error while playing a game .what does this mean?

Database Error         Message:Could not connect to server: **mysql50-54.wc2.dfw1.stabletransit.com**.         MySQL Error:User 477026_madgames already has more than 'max_user_connections' active connections        Date:Tuesday, June 14, 2011 at 11:48:32 AM         Script:[/standalone/42/checkscore]("http://www.madgam.es/standalone/42/checkscore")         Referer:[http://www.madgam.es/standalone/42/?ref=bookmarks&count=0](http://www.madgam.es/standalone/42/?ref=bookmarks&count=0)                              Database Error         Message:Could not open database: **477026_madgames**.         MySQL Error:User 477026_madgames already has more than 'max_user_connections' active connections        Date:Tuesday, June 14, 2011 at 11:48:32 AM         Script:[/standalone/42/checkscore]("http://www.madgam.es/standalone/42/checkscore")         Referer:[http://www.madgam.es/standalone/42/?ref=bookmarks&count=0](http://www.madgam.es/standalone/42/?ref=bookmarks&count=0)             
**Warning**:  mysql_real_escape_string() [[function.mysql-real-escape-string]("http://www.madgam.es/standalone/42/function.mysql-real-escape-string")]: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2) in **/mnt/stor11-wc2-dfw1/477026/www.madgam.es/web/content/includes/Database.class.php** on line **114**

**Warning**:  mysql_real_escape_string() [[function.mysql-real-escape-string]("http://www.madgam.es/standalone/42/function.mysql-real-escape-string")]: A link to the server could not be established in **/mnt/stor11-wc2-dfw1/477026/www.madgam.es/web/content/includes/Database.class.php** on line **114**
                 Database Error         Message:**MySQL Query fail:** select * from stln_games where stln_game_id = ''         MySQL Error:Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)        Date:Tuesday, June 14, 2011 at 11:48:32 AM         Script:[/standalone/42/checkscore]("http://www.madgam.es/standalone/42/checkscore")         Referer:[http://www.madgam.es/standalone/42/?ref=bookmarks&count=0](http://www.madgam.es/standalone/42/?ref=bookmarks&count=0)                              Database Error         Message:Result ID:  could not be freed.         MySQL Error:Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)        Date:Tuesday, June 14, 2011 at 11:48:32 AM         Script:[/standalone/42/checkscore]("http://www.madgam.es/standalone/42/checkscore")         Referer:[http://www.madgam.es/standalone/42/?ref=bookmarks&count=0](http://www.madgam.es/standalone/42/?ref=bookmarks&count=0)             Game not found!

---

