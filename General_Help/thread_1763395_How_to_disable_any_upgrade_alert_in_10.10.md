---
title: "How to disable any upgrade alert in 10.10?"
date: 2011-05-20
forum: General Help
---

### Post by uqbar on 2011-05-20
I'd like to avoid normal users from getting alerts about upgrading to newer Ubuntu versions.
Mostly because they are not allowed to do any upgrades.
Thanks.

---

### Post by tredegar on 2011-05-20
Looks to me as though this behaviour is set by **/etc/cron.daily/apt**

In that file it says ```
# This file understands the following apt configuration variables:
# Values here are the default.
# Create /etc/apt/apt.conf.d/02periodic file to set your preference.
[SNIP]
#  APT::Periodic::Enable "1";
#  - Enable the update/upgrade script (0=disable)
[SNIP

```

So if you created a file called **/etc/apt/apt.conf.d/02periodic** with the following entry I expect apt would no longer check for updates
```
APT::Periodic::Enable "0";
```
.... so you'll have to do it yourself, or set up your own cron job.

---

### Post by timgood on 2011-05-20
Launch Update Manager (System/Administration/Update Manager) and click on Settings on the bottom left hand corner. Enter you password. Bottom of window you will see: Release upgrade. Show new distribution releases:

Change drop down to 'Never' and close. Problem solved.

Hope this helps.

---

### Post by uqbar on 2011-06-09
This helps if only I know which system files will be modified ...
I'll try on my machine and will try to see... and update this thread.

[EDIT1] Any change is not in /etc/apt/

[EDIT2] The file is /etc/update-manager/release-upgrades

---

