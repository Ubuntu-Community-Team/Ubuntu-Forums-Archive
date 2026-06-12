---
title: "SSH help"
date: 2009-10-29
forum: General Help
---

### Post by senorgomez on 2009-10-29
I need some SSH help, I upgraded to 9.10, copied over my  sshd_config and iptable rules. Did iptables-restore and  ./init.d/ssh restart and now I am getting "Read from socket ailed: Connection reset by peer" HELP

netstat -lp shows the following

tcp        0      0 localhost:ipp           *:*                     LISTEN      -               
tcp        0      0 localhost:43167         *:*                     LISTEN      4502/beam.smp   
tcp        0      0 *: (**ssh port #**)                 *:*                     LISTEN      20216/sshd      
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      -               
tcp6       0      0 [::]: (**ssh port #**)        [::]:*                  LISTEN      20216/sshd      
udp        0      0 *:mdns                  *:*                                 -               
udp        0      0 *:51699                 *:*                                 -               
udp        0      0 *:bootpc                *:*          


Actually if someone  can explain why those other ports are listening that would be great.

---

### Post by senorgomez on 2009-10-30
Turns out I needed to restart my computer :/

I thought linux wasn't supposed to need a restart ><

---

