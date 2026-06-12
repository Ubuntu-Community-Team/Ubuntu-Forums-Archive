---
title: "how to install oracle 10 enterprise edition in ubuntu"
date: 2011-10-10
forum: General Help
---

### Post by inao on 2011-10-10
how to install oracle 10g enterprise edition in ubuntu 11.04 (32bit). i have downloaded from [http://www.oracle.com/technetwork/database/10201linuxsoft-097986.html](http://www.oracle.com/technetwork/database/10201linuxsoft-097986.html) .
thanks in advance.

---

### Post by Waappu on 2011-10-11
Hi,

This might help
[http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/](http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/)

---

### Post by raja.genupula on 2011-10-11
here is now an apt-get repository up on oss.oracle.com for XE. Just add:

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free

to /etc/apt/sources.list and then:

# wget [http://oss.oracle.com/el4/RPM-GPG-KEY-oracle](http://oss.oracle.com/el4/RPM-GPG-KEY-oracle)  -O- | sudo apt-key add - 
# apt-get update
# apt-get install oracle-xe

---

### Post by Waappu on 2011-10-11
Hi,

I think OP like install Enterprise Edition, not Express Edition of oracle database

---

