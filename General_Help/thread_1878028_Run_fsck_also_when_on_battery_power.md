---
title: "Run fsck also when on battery power"
date: 2011-11-09
forum: General Help
---

### Post by sitka.pete on 2011-11-09
Hi,
normally Ubuntu run fsck every 30 mount, but the check is disabled if the computer is running on battery power.

As I always boot my netbook on battery power, my filesystem is never checked and this cause me some troubles last day.

In the past there was an init script ***S20checkroot.sh*** where the check is performed

on_ac_power >/dev/null 2>&1
if [ "$?" -eq 1 ]
then    
        log_warning_msg "On battery power, so skipping file system check."
        rootcheck=no
fi

so I simply disable the check here.

But now with Upstart (I'm using Ubuntu 10.10) this script is no longer in use.

So, in  which script Upstart check if the computer is running on battery power to avoid to run fsck ?
I wasn't able to found it by myself.

Thanks
Sitka

---

