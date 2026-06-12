---
title: "Iptables on 10.04"
date: 2010-11-01
forum: General Help
---

### Post by kelmos on 2010-11-01
Hi,

After switching from 8.04, to 10.04 (server), I use the same iptables rules, but when restarting the service, I get the following output:

> 
root@mail:~# /etc/init.d/iptables restart
Restarting firewallUsing intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).
Using intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).
Using intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).
Using intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).
Using intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).
Using intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).
.
root@mail:~# 


Is this an iptables issue or Ubuntu? Also, it doesn't seem to break anything and I also cannot find anything via Google on this. Can anyone explain what this means please?

Thanks.
K

---

### Post by blueridgedog on 2010-11-01
The init.d iptables script appears to have a deprecated use of the negative option command.  It appears that it is correcting it as it loads the configuration.

---

### Post by kelmos on 2010-11-01
Thanks, I'll have a look at the script and see what I can find. It just bothers me that it always gives that output.

---

