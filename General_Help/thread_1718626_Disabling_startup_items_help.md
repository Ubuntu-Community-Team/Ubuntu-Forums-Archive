---
title: "Disabling startup items help"
date: 2011-03-31
forum: General Help
---

### Post by mr-woof on 2011-03-31
lo all,

Ive just ran the command netstat -ltup and I can see services running, that I dont need. I've managed to disable cups, how the heck do I disable everthing bar dhclient?

I've no idea why gdomap and squid are running for either?

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:3128                  *:*                     LISTEN      1881/(squid)    
tcp        0      0 *:gdomap                *:*                     LISTEN      1212/gdomap     
udp        0      0 *:55159                 *:*                                 1881/(squid)    
udp        0      0 *:gdomap                *:*                                 1212/gdomap     
udp        0      0 *:43044                 *:*                                 389/avahi-daemon: r
udp        0      0 *:icpv2                 *:*                                 1881/(squid)    
udp        0      0 *:bootpc                *:*                                 1795/dhclient   
udp        0      0 *:mdns                  *:*                                 389/avahi-daemon: r
udp6       0      0 [::]:42385              [::]:*                              389/avahi-daemon: r
udp6       0      0 [::]:mdns               [::]:*                              389/avahi-daemon: r

Lets start with avahi-daemon first, I've added =0 and rebooted and fecking thing is still there :)

# 1 = Try to detect unicast dns servers that serve .local and disable avahi in
# that case, 0 = Don't try to detect .local unicast dns servers, can cause
# troubles on misconfigured networks
AVAHI_DAEMON_DETECT_LOCAL=0
AVAHI_DAEMON_START=0

any ideas?

---

### Post by mr-woof on 2011-03-31
answering my own questions, ive removed avahi/squid using

sudo apt-get remove avahi-daemon
sudo apt-get remove squid

so next is gdomap, any ideas on this one?

---

### Post by mr-woof on 2011-03-31
Ive ran sudo /etc/init.d/gdomap stop which has worked, anyone know how to disable this?

---

