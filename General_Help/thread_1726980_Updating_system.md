---
title: "Updating system"
date: 2011-04-11
forum: General Help
---

### Post by mdhollis on 2011-04-11
When I update my system through the terminal it sometimes holds updates back and the only way I can install them is through the update manager.  Is there a reason for this or am I doing something wrong?

---

### Post by Redblade20XX on 2011-04-12
> **mdhollis said:**
> When I update my system through the terminal it sometimes holds updates back and the only way I can install them is through the update manager.  Is there a reason for this or am I doing something wrong?

Does the terminal say something about those packages?

---

### Post by Krytarik on 2011-04-12
Please see these articles about the difference between "apt-get *upgrade*" and "apt-get *dist-upgrade*":
[http://davitenio.wordpress.com/2008/08/24/difference-between-apt-get-upgrade-and-apt-get-dist-upgrade/](http://davitenio.wordpress.com/2008/08/24/difference-between-apt-get-upgrade-and-apt-get-dist-upgrade/)
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-upgrade](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-upgrade)
[http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/](http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/)

The bottom line is that "upgrade" only upgrades already installed packages, whereas "dist-upgrade" also installs/removes packages to meet changed dependencies of the packages to upgrade.

Greetings.

---

### Post by KegHead on 2011-04-12
Hi!

Try:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

Should work!

KegHead

---

### Post by mdhollis on 2011-04-12
Thanks.  I was using apt-get upgrade only.

---

### Post by KegHead on 2011-04-12
Hi!

Glad it worked!

Please mark your thread as solved!

KegHead

---

