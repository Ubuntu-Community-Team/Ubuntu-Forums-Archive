---
title: "problem with opera"
date: 2012-01-21
forum: General Help
---

### Post by Rainmater on 2012-01-21
hi,
my opera 11.50 client worked great but:
yesterday  I worked  with opera and i changed preferences settings,that is was my problem.
when i restarted opera it didnt start and i got "Opera needs to restart".
i upload a screenshot here:

[IMG]https://skydrive.live.com/redir.aspx?cid=54dd0e68bdcd537a&resid=54DD0E68BDCD537A!178&parid=54DD0E68BDCD537A!118[/IMG]

here its link:
[https://skydrive.live.com/redir.aspx?cid=54dd0e68bdcd537a&resid=54DD0E68BDCD537A!178&parid=54DD0E68BDCD537A!118](https://skydrive.live.com/redir.aspx?cid=54dd0e68bdcd537a&resid=54DD0E68BDCD537A!178&parid=54DD0E68BDCD537A!118)

I reinstalled it but there are a same problem now.whats problem?
please help
thanks.

---

### Post by stinkeye on 2012-01-21
Firstly try and delete your **~/.opera/operaprefs.ini** file and start opera.

If opera still won't start,if needed save your:
Bookmarks... **~/.opera/bookmarks.adr**
Mail directory...  **~/.opera/mail**
Passwords... **~/.opera/wand.dat**

Then delete the **~/.opera** folder.
Start opera and it will load with the default first run config.
No need to reinstall.

*** The tilde "~" is a shotrcut for your home directory eg /home/Rainmater
*** Folders and files preceded by a dot are hidden. In the file browser press **ctrl+h** to see hidden files and folders.

P.S Skydrive was down...what a surprise.

---

### Post by Rainmater on 2012-01-21
thanks.now it work :D

---

