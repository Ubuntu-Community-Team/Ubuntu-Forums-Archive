---
title: "Writing program to connect to vpnc"
date: 2009-09-15
forum: General Help
---

### Post by lmm5247 on 2009-09-15
at school i need to use a vpn client to connect to the internet. the school supplies a cisco vpn client with a gui, but i prefer to use vpnc through the command line because it is faster and less buggy.

the problem is, i get tired of typing all the info into the command line every time i need to connect

logan@heather-ubuntu:~$ sudo vpnc
[sudo] password for logan: 
Enter IPSec gateway address: mobility.br.psu.edu
Enter IPSec ID for mobility.br.psu.edu: pennstate
Enter IPSec secret for [email]pennstate@mobility.br.psu.edu[/email]: 
Enter username for mobility.br.psu.edu: lmm5247
Enter password for [email]lmm5247@mobility.br.psu.edu[/email]: 
resolvconf: Error: /etc/resolv.conf must be a symlink
VPNC started in background (pid: 3886)...
logan@heather-ubuntu:~$ 


is there a way i can write i litle script/program to execute when i want to connect? i'm not really a programmer so any help would be appreciated

thanks

---

