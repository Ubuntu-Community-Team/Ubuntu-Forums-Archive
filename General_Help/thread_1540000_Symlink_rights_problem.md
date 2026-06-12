---
title: "Symlink rights problem"
date: 2010-07-27
forum: General Help
---

### Post by snarf77 on 2010-07-27
Hello everybody,

I'm trying to configure a cluster HA based on Drbd synchro and corosync.
everything was going ok with this config (I thought having done the hardest part !!) but I'm now stuck with (I think) a stupid problem of symlink (I'm really not used to use them so excuse in advance the level of this question but I can't really find a solution elsewhere..)

Indeed, I need to move the conf file of a service (dhcp3) onto my replicated drdb location and I installed the following symlink:

sudo ln -l /replicated/dhcp/dhcpd.conf /etc/dhcp3/dhcpd.conf
(/replicated being the mount point of my drbd storage)

When doing this dhcp3 server is unable to start because "permission denied" on dhcpd.conf file.
As I'm far from being expert, I tried to troubleshoot and discovered that depending on the target file location the link is sometime ok (for ex in : /etc/dhcp3/test or even /etc/) and sometime not (for ex if it is located at root (/) or in another partition (drbd)).

I force the attributes right for the target file to 777 (and even to the symlink event if I know it is useless) jsut to try but nothing is working.

What can I do to finally store my conf file in my replicated location ?

thanks in advance for your help.

Snarf

---

