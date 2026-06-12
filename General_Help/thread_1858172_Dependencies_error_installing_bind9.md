---
title: "Dependencies error installing bind9"
date: 2011-10-11
forum: General Help
---

### Post by cbraxton on 2011-10-11
When trying to "apt-get install bind9" on Ubuntu Server 10.04.3, the following error occurs:

```

The following packages have unmet dependencies:
  bind9: Depends: libbind9-60 (= 1:9.7.0.dfsg.P1-1) but 1:9.7.0.dfsg.P1-1ubuntu0.3 is to be installed
         Depends: libdns64 (= 1:9.7.0.dfsg.P1-1) but 1:9.7.0.dfsg.P1-1ubuntu0.3 is to be installed
         Depends: libisc60 (= 1:9.7.0.dfsg.P1-1) but 1:9.7.0.dfsg.P1-1ubuntu0.3 is to be installed
         Depends: libisccc60 (= 1:9.7.0.dfsg.P1-1) but 1:9.7.0.dfsg.P1-1ubuntu0.3 is to be installed
         Depends: libisccfg60 (= 1:9.7.0.dfsg.P1-1) but 1:9.7.0.dfsg.P1-1ubuntu0.3 is to be installed
         Depends: liblwres60 (= 1:9.7.0.dfsg.P1-1) but 1:9.7.0.dfsg.P1-1ubuntu0.3 is to be installed
E: Broken packages

```

Running "apt-get install -f" to fix broken packages does not help. It looks like there is a discrepancy in the package names. How to fix this?

---

### Post by collisionystm on 2011-10-11
maybe try a force install?
 
sudo apt-get install --force-all bind9
 
Then remove it
 
sudo apt-get purge bind9
 
then reinstall like normal

---

### Post by cbraxton on 2011-10-12
I gave up and installed dnsmasq instead. (The "--force-all" option was not recognized by apt-get and after many Google searches I was unable to find a solution to this strange dependency problem. Fortunately it seems restricted to the bind9 package, at least so far.)

Dnsmasq is much simpler and works fine for a small LAN, I'm just more accustomed to bind.

---

