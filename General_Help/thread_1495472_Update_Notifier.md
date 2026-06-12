---
title: "Update Notifier"
date: 2010-05-28
forum: General Help
---

### Post by sdalgl72 on 2010-05-28
I have 10.04 and I have noticed that it doesn't notify me when updates are available even though it is set to is there anything I can do to fix this problem?  Is anyone else experiencing it?

---

### Post by plucky on 2010-05-28
> **sdalgl72 said:**
> I have 10.04 and I have noticed that it doesn't notify me when updates are available even though it is set to is there anything I can do to fix this problem?  Is anyone else experiencing it?

From the Lucid Release Notes:-
> Change in notifications of available updates

Ubuntu 10.04 LTS launches update-manager directly to handle package updates, instead of displaying a notification icon in the GNOME panel. Users are notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

(This change was made in Ubuntu 9.04.) 

Got my first security updates two days ago.All the previous ones were only recommended updates and are only notified once a week by placing an "Update Manager" window in the windows list on the bottom panel.

Good Luck

---

### Post by sdalgl72 on 2010-05-28
Cheers sorry hadn't seen that will keep it as it is then.

---

