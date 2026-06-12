---
title: "Trying to remove apache but it install apache dependencies"
date: 2011-02-27
forum: General Help
---

### Post by slooksterpsv on 2011-02-27
Ok so I do:

sudo apt-get purge apache2.2-common - and it does this:

```

sudo apt-get purge apache2.2-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-prefork libapache2-mod-php5filter
Suggested packages:
  php-pear
The following packages will be REMOVED:
  apache2-mpm-itk* libapache2-mod-php5*
The following NEW packages will be installed:
  apache2-mpm-prefork libapache2-mod-php5filter
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 3,107kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

I try to purge all of apache from my system and it reinstall stuff and won't remove apache2. So like this:

```

sudo apt-get remove apache2-utils apache2.2-bin apache2.2-common apache2-mpm-itk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2.2-common : Depends: apache2-utils but it is not going to be installed
E: Broken packages

```

So what is up with that? Even with --force-yes, it still doesn't work.

---

### Post by slooksterpsv on 2011-02-27
Haha so I had to use:

sudo dpkg -r --force-all ...

for all of the apache2 and libapache items. Something weird is happening there, maybe a faulty metadata package?

---

### Post by nickmcg on 2011-02-27
Do you need to run dpkg on each package individually, or can wild cards be used?

Cheers

Nick

---

### Post by slooksterpsv on 2011-02-27
> **nickmcg said:**
> Do you need to run dpkg on each package individually, or can wild cards be used?

Cheers

Nick

I did individual cause an accidental wildcard (if it works) could damage your system to where it needs to be reinstalled.

---

### Post by nickmcg on 2011-02-28
Thanks

Nick

---

