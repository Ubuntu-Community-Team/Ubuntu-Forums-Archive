---
title: "Busted a production servers PHP"
date: 2011-04-03
forum: General Help
---

### Post by dazman19 on 2011-04-03
Hi,

This is actually a debian server, but i thought someone here could help me with it.

We needed to upgrade php to 5.3+ because we wrote some cool new code using then new static functions in 5.3. But we have busted our server big time.

I cant get php to work anymore:
I have tried to clean it up, And install each package manually but most of them just bomb out. With a similar message. I need to get the PHP running on the server ASAP. 

daryl@EzyServer:/$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5: Depends: libapache2-mod-php5 (>= 5.3.5-0.dotdeb.1) but it is not going to be installed or
                 libapache2-mod-php5filter (>= 5.3.5-0.dotdeb.1) but it is not going to be installed or
                 php5-cgi (>= 5.3.5-0.dotdeb.1) but it is not going to be installed or
                 php5-fpm (>= 5.3.5-0.dotdeb.1) but it is not going to be installed
E: Broken packages

Any help would be appreciated.

---

### Post by chupnik on 2011-04-23
> **dazman19 said:**
> Hi,

This is actually a debian server, but i thought someone here could help me with it.

We needed to upgrade php to 5.3+ because we wrote some cool new code using then new static functions in 5.3. But we have busted our server big time.

I cant get php to work anymore:
I have tried to clean it up, And install each package manually but most of them just bomb out. With a similar message. I need to get the PHP running on the server ASAP. 

daryl@EzyServer:/$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5: Depends: libapache2-mod-php5 (>= 5.3.5-0.dotdeb.1) but it is not going to be installed or
                 libapache2-mod-php5filter (>= 5.3.5-0.dotdeb.1) but it is not going to be installed or
                 php5-cgi (>= 5.3.5-0.dotdeb.1) but it is not going to be installed or
                 php5-fpm (>= 5.3.5-0.dotdeb.1) but it is not going to be installed
E: Broken packages

Any help would be appreciated.
Ubuntu 10.10 Maverick comes with PHP 5.3.3.
If you need to install a newer version of PHP than 5.3.3 you will need to add third-party PPA archive, such as this one [https://launchpad.net/~verwilst](https://launchpad.net/~verwilst).
Using the PPA archives from DotDeb.org for Ubuntu is not good practi&#1089;e which is causing conflicts during package installation. Of course, it is possible to solve this issue by installing additional libraries, but easier to use appropriate Ubuntu-ready PPA.

---

