---
title: "php5 modules not loading correctly after update to 10.10"
date: 2010-10-22
forum: General Help
---

### Post by metal.lunchbox on 2010-10-22
I recently upgraded to 10.10 desktop 64 bit from 10.04 and was running a test lighttpd webserver with php5 and mysql. everything worked just fine until upgrade. After the upgrade the webserver worked fine but my installed php modules, notably mysql, are not loading correctly. phpinfo() reports lots of info but mysql and curl extensions do not show up. According to the package manager both are installed. I don't care about understanding the problem if I can just make the system work. I used aptitude purge to remove lighttpd, php5, mysql-client, mysql-server and all php related packages from the computer. I then deleted any leftover configuration files from /etc/ . I reinstalled these applications and have not seen any change. php5-curl and php5-mysql packages are installed but these extensions are not loading. Can anyone provide a clue? what might I try to get these working again? What might be going wrong?

---

