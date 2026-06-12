---
title: "AlternC on ubuntu jaunty HELP"
date: 2010-03-27
forum: General Help
---

### Post by stilling on 2010-03-27
i whant to install AlternC hosting control panel on my ubuntu jaunty machine all went well i added the repos that are provided on the alternc website i run the
sudo aptitude update command
and
sudo apt-get install alternc command

BUT PROBLEM

The following packages have unmet dependencies:
  alternc: Depends: proftpd-mysql but it is not installable
           Recommends: libapache-mod-gzip but it is not installable
           Recommends: apache-ssl but it is not installable
E: Broken packages


i tried to install proftpd for the "proftpd-mysql" that i know is the module
Please provide me some ideeas 

no ehcp
no webmin 
no vhcs
no plesk
others 

i discoverd that alternc is really easy to use control panel 
and i really whant to install this one 


Thanks in advance

---

### Post by gmargo on 2010-03-27
The AlternC pre-built packages that you are attempting to install are built against Debian Etch.  So it is natural that some of the dependencies cannot be resolved in Ubuntu. You need to either compile from source, or install Debian Etch.

Here are the sources used to build the packages: [http://debian.alternc.org/dists/stable/main/source/admin/](http://debian.alternc.org/dists/stable/main/source/admin/).  It will probably be a simple task to compile them.

---

### Post by stilling on 2010-03-28
Ok on ly old laptop i installed Debian Lenny and surprise full of  errors and no install of alternc succeed so .... i will change it i reviewd the other possible Control Panels and web-cp is my second alternative so 
 


Thanks so much for your quick answer

---

