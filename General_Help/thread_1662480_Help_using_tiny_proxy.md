---
title: "Help using tiny proxy"
date: 2011-01-08
forum: General Help
---

### Post by jsriz on 2011-01-08
I am trying to set tinyproxy on my laptop and have sucessfully installed and edited the .conf file to listen on port 12345
and i run it by using /sbin/tinyproxy
i am dropped to a new terminal
when i nmap my system i get the following:
```
Host is up (0.00069s latency).
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds

```
and when i connect try to connect to my laptop by using my ip and 12345 as port number in 'http proxy' feild it does not proxy.
How do i test if tiny proxy is working or not

---

### Post by jsriz on 2011-01-09
anyone???

---

### Post by binoplaza on 2011-01-09
Did you check if the process is still running? It might have crashed soon after you started it.

Look for a process:

```

Ps -audio¦ grep tiny proxy

```

Ps: you can use "netstat" on the host that runs tiny proxy to check of it's listening on any port

---

