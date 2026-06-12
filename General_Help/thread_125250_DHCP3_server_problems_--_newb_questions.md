---
title: "DHCP3 server problems -- newb questions"
date: 2006-02-03
forum: General Help
---

### Post by Lerris on 2006-02-03
All right - a disclaimer - I'm new to the Linux server world so don't assume I know anything.

  I'm trying to set up my Ubuntu box as my DHCP/DNS server. I installed DHCP3 and it's running. I can get a lease from my XP laptop but after the lease expires (every 10 minutes or so) the internet stops working on my XP box. The XP box claims it has a new lease but it's not able to go anywhere without a release and renew of the ip.

  I don't know where the log files are for DHCP3 and googling for some help hasn't produced anything yet.

  Here's the important part of my dhcp config:
# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.200;
  option domain-name-servers 192.168.1.1;
  option domain-name "ehi.int";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 86400;

  authoritative;
  ddns-updates on;
}

  I know I could just increase the max-lease-time but even if I set it to three days I don't want to have it cut out on me after 3 days.

  Any help would be greatly appreciated.

---

### Post by Lerris on 2006-02-03
Well... it seems to have resolved itself. I don't know what I did but now my XP machine is not dropping off. Still don't know how to monitor the thing though.

---

### Post by dcstar on 2006-02-03
[QUOTE=Lerris]Well... it seems to have resolved itself. I don't know what I did but now my XP machine is not dropping off. Still don't know how to monitor the thing though.[/QUOTE]
Look in the /var/log syslog or messages files, or the DHCP could create its own log file there.

---

