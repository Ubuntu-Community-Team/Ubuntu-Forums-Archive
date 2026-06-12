---
title: "netcat does not work"
date: 2011-04-28
forum: General Help
---

### Post by uzee007 on 2011-04-28
Hi Guys,
I have ubuntu 10.10 running on 2 machines, the netcat installed is the netcat-openbsd. I'm unable to establish a connection between the two. However it works on the localhost. For example:
On machine 1:
If I use tcpdump with any port say 2020 and on the same machine in another window I use "nc localhost 2020", I see an output but if I do this from machine 2, like "nc machine1 2020", there is nothing, and after a while it says connection timed out.
(netcat: connect to machine1 port 2020 (tcp) failed: Connection timed out)
I have also tried uninstalling netcat-openbsd and installing netcat and netcat-traditional, but still the same, infact with these ones, it doesn't even work on the localhost. I have checked iptables and they are the server default which is to allow all.

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Any ideas....?
Thanks much
uzee

---

### Post by uzee007 on 2011-05-01
Guys..... anyone ??

---

