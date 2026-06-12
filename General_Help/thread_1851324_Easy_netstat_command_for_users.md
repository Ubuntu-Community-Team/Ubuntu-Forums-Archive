---
title: "Easy netstat command for users"
date: 2011-09-28
forum: General Help
---

### Post by rng on 2011-09-28
netstat is said to be a very useful command for finding which programs are connected to the network/internet. But it has a large number of options and a long output, much of which is not relevant to this aspect. I have been suggested following options which seem to give a brief relevant output where the rightmost column shows the programs that have active connections to the network: 

sudo netstat -lput

(l=listening, p=program-name, u=udp and t=tcp connections)

Following is an example output: 

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      2054/cupsd      
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      2054/cupsd      
udp        0      0 *:55443                 *:*                                 1190/avahi-daemon: 
udp        0      0 *:bootpc                *:*                                 2934/dhclient   
udp        0      0 *:mdns                  *:*                                 1190/avahi-daemon: 
```

I will appreciate if some expert would comment if these options are sufficient or some other combination is better.

---

### Post by Sazhen86 on 2011-09-28
That output only shows those processes that are listening for connections, not those that have established connections, which I suspect is what you want.

I'd suggest netstat -aut to list all endpoints, both established and listening.

---

### Post by rng on 2011-09-28
I agree. But -p option should be there so that program-name is displayed. So the command should be: 

sudo netstat -aput

(-a = all)

The command works without 'sudo' also but then all program names are not displayed (only user-owned programs are displayed).

---

### Post by rng on 2011-10-01
To monitor regularly (every 60 secs in this example) one can give following command in a terminal: 

sudo watch -n 60 "netstat -aput"

---

### Post by rng on 2011-10-23
Adding -e option shows owner of programs also:

sudo netstat -apute

---

