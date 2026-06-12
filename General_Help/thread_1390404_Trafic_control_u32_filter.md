---
title: "Trafic control u32 filter"
date: 2010-01-25
forum: General Help
---

### Post by urosh2 on 2010-01-25
Hello.
I hope someone could help me with my problem with tc.

I am struggling to get the right mask for source ports. I want to limit incoming traffic from all ips, but not from source port 10000 to 20000. For now i have this.

tc qdisc del dev wlan0 handle ffff: ingress
tc qdisc add dev wlan0 handle ffff: ingress
tc filter add dev wlan0 parent ffff: protocol ip prio 50 u32 match ip sport 10000 0x???? police continue flowid :1
tc filter add dev wlan0 parent ffff: protocol ip prio 50 u32 match ip src 0.0.0.0/0 police rate 800kbit burst 10kbit action drop flowid :3

What is the right mask for sport, so that it will match from 10000 to 20000?:confused:

One did explain how to do it here [http://bugs.gentoo.org/81383](http://bugs.gentoo.org/81383) but 0x96CF is not the right mask. 
I am testing this with these commands:

sender pv /dev/zero | nc 192.168.100.111 -p 20000 2224
receiver nc -v -v -l -p 2224 >/dev/null

Thank you.

---

### Post by urosh2 on 2010-01-27
Bump.

---

