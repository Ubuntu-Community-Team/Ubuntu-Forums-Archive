---
title: "Is the Update Manager working for anybody?"
date: 2010-05-16
forum: General Help
---

### Post by Rifester on 2010-05-16
Is the update manager working in 10.04 for anybody?  I have not been notified of any updates (has something changed in the way updates work?)  I have double checked that check daily is selected.  I manually check for updates and find them, but the system never notifies me.   I also checked launchpad and could not find anything in relation to this problem.   Is it just my set up?

---

### Post by lisati on 2010-05-16
Have you opened it up with System->Administration->Update Manager?

---

### Post by todak on 2010-05-16
Run *gconf-editor*. Look under */apps/update-notifier*. Make sure the  *auto_launch* box is not ticked and then the notifier will appear in the tray when updates are available.

From the [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004) page:

> Change in notifications of available updates

  

Ubuntu 10.04 LTS launches update-manager directly to handle package updates, instead of displaying a notification icon in the GNOME panel. Users are notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.   

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:   

  

gconftool -s --type bool /apps/update-notifier/auto_launch false

---

### Post by QIII on 2010-05-16
Interestingly, I just looked and found out that update-notifier is not installed on my machine.

I guess I hadn't noticed since I update via the terminal daily.  (Hence, I don't care if it's there...)

You might check that update-notifier is installed (If it isn't, let me know.  Maybe this is something to check in to.)

From there, change the settings.

---

### Post by Rifester on 2010-05-17
Todak, 
Thanks for the info!  Update notifier is installed on my system.  I was not aware that Lucid did not notify of us of updates more then weekly. 

Rifester

---

