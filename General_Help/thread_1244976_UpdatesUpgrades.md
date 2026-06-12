---
title: "Updates/Upgrades?"
date: 2009-08-20
forum: General Help
---

### Post by virtualu2 on 2009-08-20
Hello,
I am trying to figure out the best and most recommended way to upgrade my new 9.04 install?  I know of synaptic, adept, apt-get dist-upgrade, aptitude, so what is the best and most stable method?

I ran just the regular updates after I did this new install, but I didn't get the new kernel and so forth.  So how do I do that safely?

---

### Post by rcayea on 2009-08-20
Are you asking, what is the safest way to upgrade software you already have on your system?

If so, I think Synaptic is fine. If you really wanted to get fussy you could just be sure you install Canonical maintained software/updates.

---

### Post by wojox on 2009-08-20
What kernel version did you receive?

---

### Post by bionnaki on 2009-08-20
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

---

### Post by mcduck on 2009-08-20
> **virtualu2 said:**
> Hello,
I am trying to figure out the best and most recommended way to upgrade my new 9.04 install?  I know of synaptic, adept, apt-get dist-upgrade, aptitude, so what is the best and most stable method?

I ran just the regular updates after I did this new install, but I didn't get the new kernel and so forth.  So how do I do that safely?

They are all just different interfaces to the same package manager (apart from Aptitude, which uses dpkg to install the package like the others, but handles dependencies slightly differently from apt-get), so it doesn't make any difference. Use which one you like best.

---

### Post by 3rdalbum on 2009-08-20
The Update Manager program is the officially-recommended way to update your system. If you didn't recieve a kernel update, check that you have the appropriate software sources enabled in System > Administration > Software Sources.

---

### Post by Copernicus1234 on 2009-08-20
Upgrade? Are you sure you dont mean update?

Upgrade = switch to alpha of Ubuntu 9.10
Update = get all the patches and updates for Ubuntu 9.04.

---

### Post by mcduck on 2009-08-20
> **Copernicus1234 said:**
> Upgrade? Are you sure you dont mean update?

Upgrade = switch to alpha of Ubuntu 9.10
Update = get all the patches and updates for Ubuntu 9.04.

It''s not exactly that straight.

Considering that the commands used for installing updates for your current release versions are "apt-get upgrade" and "apt-get dist-upgrade" (and neither one of these commands will upgrade to next release version, like from 9.04 to 9.10)

"sudo apt-get upgrade" updates your installed packages, and if required, also install new packages (for example if latest version of some package has new dependency). Updating with the Update Manager is exactly the same as running this command.

"sudo apt-get dist-upgrade" is the same as above, but it's also able to remove packages it that's necessary. For example if several packages have been merged into one, the old ones must be removed  and new one installed instead. Updating through Synaptic Package manager works like this.

(and the command to upgrade to next release version is "sudo do-release-upgrade". e Update Manager will also handle the same task, if suitable release upgrade is available)

---

