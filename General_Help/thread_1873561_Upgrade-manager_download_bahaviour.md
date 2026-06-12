---
title: "Upgrade-manager download bahaviour"
date: 2011-11-01
forum: General Help
---

### Post by Gillingham on 2011-11-01
I have 2 issues with update manager:

1) How do I get update manager to download ALL updates automatically when it is run at 5am (while I have free bandwidth) rather than just the security updates?

2) How do I get the notification icon back into the systray where it belongs and I can see it immediately? (and yes I have whitelisted all programs.)  Alternatively is there a file I can read to put the details into conky?

Thank you for your help.

David

---

### Post by Gillingham on 2011-11-02
bump..

---

### Post by Gillingham on 2011-11-13
OK by editing 
```
/etc/apt/apt.conf.d/50unattended-upgrades
```
to uncomment the lines:
```
	"${distro_id} ${distro_codename}-updates";
	"${distro_id} ${distro_codename}-proposed";
```
allowed me to solve question 1.

Any ideas on number 2 to get the notification back into the systray?

David

---

### Post by hungrybelly on 2012-01-05
You might try the solution in [http://ubuntuforums.org/showthread.php?t=1873817&highlight=update+manager+notification](http://ubuntuforums.org/showthread.php?t=1873817&highlight=update+manager+notification).

I don't actually understand it, and am not sure if it restores the notification or just stops the auto-launch, but the OP was satisfied.

---

