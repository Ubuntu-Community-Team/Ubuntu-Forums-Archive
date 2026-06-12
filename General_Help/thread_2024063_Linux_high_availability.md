---
title: "Linux high availability"
date: 2012-07-13
forum: General Help
---

### Post by butleredwin on 2012-07-13
Hi There

I am new to Linux high availability and would like to have a setup that keeps my severs up 99.999% of the time.

This will be servers that will be running Ubuntu 12.04 LTS Server with Apache and PostgresSQL as the database.

I did some reading under the Linux-HA (heartbeat) project but it seems a bit out dated? So I saw a post that said that I should rather use Corrosync as the heartbeat messaging layer.

Is corrosync the answer to use with pacemaker on Ubuntu 12.04? 

I am not entirely sure how all the dots connect so here is how I understand it:

To setup a High availability server I need.

Messaging layer

* Heartbeat OR corosync

Deamon/service

* Pacemaker
Not sure what openAIS is

data sharing

* DRBD or some kind of NFS share that syncs. I know rsync is not the best solution for this.


So basically what I what is one IP that switches between 2 - 4 + nodes if the main server fails ( IP failover), The servers must load balance, I DO NOT want to use external storage like SAN and NAS devices ( local storage that is on RAID), Needs to run on Uuntu 12.04 server. 

Most documentations is only RHEL and fedora. I need it for Ubuntu

Please help me, 

I thank you in advance.

---

### Post by Cheesemill on 2012-07-13
This article may give you some pointers:

[https://library.linode.com/linux-ha/ip-failover-heartbeat-pacemaker-drbd-mysql-ubuntu-10.04](https://library.linode.com/linux-ha/ip-failover-heartbeat-pacemaker-drbd-mysql-ubuntu-10.04)

---

### Post by butleredwin on 2012-07-15
Thank you. Will give feedback when I get stuck

---

