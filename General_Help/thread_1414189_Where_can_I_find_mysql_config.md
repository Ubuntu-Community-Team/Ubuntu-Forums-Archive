---
title: "Where can I find mysql_config?"
date: 2010-02-23
forum: General Help
---

### Post by esauer on 2010-02-23
I am trying to install the MySQLdb package for python and the instructions tell me that I need to add mysql_config to my path. This file does not appear to exist in my mysql installation, or anywhere on my machine. I installed mysql-server from the ubuntu package manager, and then did a search of my system for that file.
```
sudo find / -name mysql_config
```
This gave me no results. Can someone tell me where I can find this? Is it part of some extra toolkit for mysql?

Thanks

---

### Post by gmargo on 2010-02-23
Install the **libmysqlclient-dev **package.

You can search for specific files on the packages page: [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by esauer on 2010-02-23
Perfect, thanks!

---

