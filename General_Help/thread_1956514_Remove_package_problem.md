---
title: "Remove package problem"
date: 2012-04-11
forum: General Help
---

### Post by teriyaki-89 on 2012-04-11
hi everybody i am trying to remove some packeges like 

dpkg -l | grep krb
ii  **libgssapi-krb5-2 **    1.9.1+dfsg-1ubuntu2.2      MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  l**ibkrb5-3 **                 1.9.1+dfsg-1ubuntu2.2      MIT Kerberos runtime libraries
ii ** libkrb5support0    ** 1.9.1+dfsg-1ubuntu2.2      MIT Kerberos runtime libraries - Support library
but i met some dependencies that i do not understand. **What should i do?**



The following packages have unmet dependencies:
 apache2-mpm-prefork : Depends: apache2.2-bin (= 2.2.20-1ubuntu1.2) but it is not going to be installed
 apache2.2-common : Depends: apache2.2-bin (= 2.2.20-1ubuntu1.2) but it is not going to be installed
 kde-runtime : Depends: libkdewebkit5 (>= 4:4.6) but it is not going to be installed
               Depends: libkhtml5 (>= 4:4.6) but it is not going to be installed
               Depends: libkmediaplayer4 (>= 4:4.6) but it is not going to be installed
               Depends: libkparts4 (>= 4:4.6) but it is not going to be installed
               Depends: libnepomuk4 (>= 4:4.6.1) but it is not going to be installed
               Depends: libnepomukquery4a (>= 4:4.6) but it is not going to be installed
               Depends: libplasma3 (>= 4:4.6.80) but it is not going to be installed
               Depends: libsmbclient (>= 2:3.2.0) but it is not going to be installed
               Depends: libsoprano4 (>= 2.6.51) but it is not going to be installed
               Depends: kdelibs5-plugins (>= 4:4.6.80) but it is not going to be installed
               Depends: plasma-scriptengine-javascript (= 4:4.7.4-0ubuntu0.1) but it is not going to be installed
               Recommends: virtuoso-minimal but it is not going to be installed
               Recommends: kubuntu-debug-installer but it is not going to be installed
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
 libkio5 : Depends: libnepomuk4 (= 4:4.7.4-0ubuntu0.1) but it is not going to be installed
           Recommends: kdelibs5-plugins (= 4:4.7.4-0ubuntu0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by raja.genupula on 2012-04-11
open your terminal 
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install -f
```

While executing upgrade and dist upgrade if you got anything like dependencies issue then do sudo apt-get install -f , i mean the last command . so if all went fine then you can remove the App what  you want  to remove . 


hope that helps.
all the best .,

---

### Post by teriyaki-89 on 2012-04-11
thanks but did not help i meant how to solve dependencies problems with my packages.
 Should i uninstall all dependecy met packages to succeed remove needed package?

---

### Post by raja.genupula on 2012-04-11
what you got after 
```
sudo apt-get install -f
```


install -f will deals with getting dependencies . 
if that wont help you then do as 
```
sudo apt-get remove -f
```

Then try again . 

all the best .

---

