---
title: "unattended-upgrades script not installing upgrades"
date: 2012-08-14
forum: General Help
---

### Post by tbharber on 2012-08-14
Hey All,

I just rolled a new Ubuntu 12.04 sever.  The issue I am having is that after installing the unattended-upgrades script, it will not automatically install updates.  

When logging in, it will state there are updates available to be installed at least once a week.  I can manually install these upgrades, but would like this completed automatically.

The status each day in */var/log/unattended-upgrades* is:
"no packages found that can be upgraded unattended"

I have my /etc/apt/apt.conf.d/10periodic file updated correctly:
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```



I have had a Ubuntu 11.04 server in the past running for over a year and have never had this issue.  It always installs the updates without manual intervention.

Any thoughts?

---

