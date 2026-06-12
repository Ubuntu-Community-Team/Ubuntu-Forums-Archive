---
title: "mysql can't start"
date: 2010-12-28
forum: General Help
---

### Post by IamNot on 2010-12-28
I have a problem recently I followed the current guide to change mysql database default dir: [http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html](http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html) so I could move my databases to another storage using iscsi. The problem is that mysql server won't start up now because it gives can't connect trough sock error. I checked that the new location dir isn't owned by the mysql user so I thought that would be the problem. When I try to change the owner of the file I can't (even with sudo) the command doesn't fail, it just won't get changed. What I'm wondering is if it could be related and if you have any idea of why it won't change. Thank you. I'm using ubuntu 9.04 by the way.

---

