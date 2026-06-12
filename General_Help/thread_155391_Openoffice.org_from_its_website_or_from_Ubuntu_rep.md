---
title: "Openoffice.org from its website or from Ubuntu repositories?"
date: 2006-04-05
forum: General Help
---

### Post by Marcos.Rufino on 2006-04-05
When installing Openoffice.org, what's the difference between the versions offered by Ubuntu repos from the one in Openoffice.org official website?

I know that Openoffice.org from the repos is a customized version to work smoothly in Ubuntu. But what does this really mean?

---

### Post by aysiu on 2006-04-05
It means it's easier to update. When Ubuntu updates OpenOffice, all you need to do is ```
sudo apt-get update
sudo apt-get dist-upgrade
``` To upgrade the one from OpenOffice wouldn't be as simple.

---

### Post by MartinG on 2006-04-05
On the other hand, I've had issues with the debs from Ubuntu -- missing features etc., to the extent that I've switched to the "official" debs, from:
[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/)

---

### Post by RikoW on 2006-04-05
Upgrading OOo from the OOo website isn't really that hard. I did it several times already without any problems. It's a bit more work of course than the two apt-get's above, true, but there are plenty of posts around in the forum which tell you how-to.

The real disadvantage of doing it yourself compared to using the repos is in my opinion, that you have to go a check for update/upgrades yourself and don't let the Ubuntu team worry about it and notify you via the update notification.

But then again: in this case it's usually not critical not to keep always up to date ....

Cheers,

           Riko

---

