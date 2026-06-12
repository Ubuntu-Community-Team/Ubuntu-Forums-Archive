---
title: "Incoming network connections disabled?"
date: 2012-08-17
forum: General Help
---

### Post by jJackFlash on 2012-08-17
Hi,

I have a headless server running 10.04.2. I normally manage it from my desktop through ssh. For some days I've seen the restart required message but I ignored it until yesterday when suddenly I wasn't able to log in through ssh (Operation time out). Appletalk File Server wasn't working either. I thought it was probably hanged and I did a hard reset. Same problems. Finally I plugged in a monitor and was able to log in and have a look. Apparently everything is OK except the system seems to be ignoring all incoming connections. No ssh, no ping, no AFP, no Mediatomb web access, no transmission web access.

I checked:
- ping is allowed ( /proc/sys/net/ipv4/icmp_echo_ignore_all -> 0).
- ufw status -> inactive
- aparently the listeners are there but incoming requests are being ignored
- output connections seem to be OK: I'm able to ping LAN & WAN hosts, even transmission keeps uploading stuff
- syslog: there is an error regarding ssh: init: ssh main process (731) terminated with status 255, Don't think it can explain the other incoming connection problems
- started tcpspy (tcpspy -d) and tried to ssh to the server. I could only see transmission outgoing connections being logged.

Any help would be appreciated.

Thanks,
jj

---

### Post by jJackFlash on 2012-08-17
Solved. The router was the problem. It needed a restart.

Thanks anyway,
jj

---

