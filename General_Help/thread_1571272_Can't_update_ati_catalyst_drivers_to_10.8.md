---
title: "Can't update ati catalyst drivers to 10.8"
date: 2010-09-09
forum: General Help
---

### Post by IvoP123 on 2010-09-09
I had catalyst 10.6 drivers and then i uninstalled it (by running fglrx-uninstall.sh). After that, I installed 10.8 version downloaded form ati.amd.com, but when I open catalyst control center it still says I have 10.6 installed. What is the problem?

---

### Post by timuckun on 2010-09-14
> **IvoP123 said:**
> I had catalyst 10.6 drivers and then i uninstalled it (by running fglrx-uninstall.sh). After that, I installed 10.8 version downloaded form ati.amd.com, but when I open catalyst control center it still says I have 10.6 installed. What is the problem?

I am getting the exact same problem.

---

### Post by IvoP123 on 2010-09-17
> **timuckun said:**
> I am getting the exact same problem.

I think i managed to solve this. After uninstall i deleted folders :

./usr/src/ati
./dev/ati
./etc/ati
./proc/ati

Than i installed 10.8 and everything was OK ;)

---

