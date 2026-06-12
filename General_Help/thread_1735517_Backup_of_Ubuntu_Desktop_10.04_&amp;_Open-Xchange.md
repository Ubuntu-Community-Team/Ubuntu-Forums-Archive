---
title: "Backup of Ubuntu Desktop 10.04 &amp; Open-Xchange"
date: 2011-04-21
forum: General Help
---

### Post by iamnotyou on 2011-04-21
Not sure which category this best fits so trying general help :) I'm trying to backup Open-Xchange

I've setup a fresh install of **Ubuntu Desktop 10.04** with all the available updates (as of last night). **Open-Xchange 6 Community** is installed, configured, & tested. Works great and ready for the staff to start using.

I just need to configure a daily backup. Grabbed **"Back in Time"** from the Software center and found this telling me what I need to backup **[http://oxpedia.org/wiki/index.php?title=Open-Xchange_backup](http://oxpedia.org/wiki/index.php?title=Open-Xchange_backup)**

Am still very much a newbie at this and slightly befuddled by this part about backing up the database:
> **Database**

For the Database, the standard mysql tools can be used for a backup. If mysqldump is used to back up the database, following parameters are recommended:

mysqldump -&#8211;all-databases -&#8211;single-transaction

Is just backing up everything under /opt/open-xchange/ enough or do I need to do something else to copy the database?

---

### Post by iamnotyou on 2011-04-21
I think I've got it figured out. At least a clearer (though still limited) idea of what I'm doing :)

Haven't tested anything yet. But if I understand correctly it sounds like I need to dump the MySQL database before "Back in Time" runs. Then it can backup that file along with /opt/open-xchange/.

---

