---
title: "Random freeze in boot process"
date: 2009-08-10
forum: General Help
---

### Post by Elv13 on 2009-08-10
Hi, 

I am having trouble getting a stable ubuntu version to push on some corporate workstations. It boot fine around 98% of time but fail for no reason on the 2 other %. It happen most of time on HP Z600 octo core 12gb ram corporate workstation but (may) have been saw in virtualbox and AIMB ITX board too (never saw it myself but my colleague have). 

The problem come from different (related) sources: mysql, samba and nfs (both common and kernel). 

When it fail, some or all of these services timeout after the 20 attempt (5 hours * number of failure). MySQL fail at 
```
ping_output=`$MYADMIN ping 2>&1`; ping_alive=$(( ! $? )) 
```
in /etc/init.d/mysql while others fail at  start-stop-deamon. Both command return nothing interesting in $?, stdout, $ping_output nor stderr. I have no idea where this random problem come from. Networking seem to be a common factor in all those services, but "networking" itself is up and running. I am not using NetworkManager and /etc/rules.d/ are not that far from standard ones.

---

### Post by Elv13 on 2009-08-14
up

---

