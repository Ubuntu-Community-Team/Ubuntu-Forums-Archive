---
title: "Strange stunnel4 problem"
date: 2010-04-10
forum: General Help
---

### Post by new_tolinux on 2010-04-10
I have installed stunnel4, but it won't work at boot (although it starts).
The config shouldn't be the problem, since a manual restart (sudo /etc/init.d/stunnel4 restart) makes it work.

I already changed the startup order by:
```
sudo update-rc.d -f stunnel4 remove
sudo update-rc.d stunnel4 defaults 99
```
But after every reboot:
```
telnet localhost 2830
```result:
```
Trying ::1...
Trying 172.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
```Then:
```
sudo /etc/init.d/stunnel4 restart
```Result:
```
Restarting SSL tunnels: [stopped: /etc/stunnel/stunnel.conf]  [Started: /etc/stunnel/stunnel.conf] stunnel.
```After that:
```
telnet localhost 2830
```result:
```
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
200 news.myusp NNRP Service Ready (posting ok) (yEnc  enabled).
```

How do I make it work without restarting the daemon manually?

---

### Post by houserparker on 2010-04-12
I am having the same problem and have researched this for days, finding other people with same problem but with no solution.

Anyone correct me if I'm wrong but from what a have gathered so far this is caused by the daemon looking up a DNS that doesn't exist until the system has logged in and the user has entered their password to access (in most cases) their wireless network. This is why restarting stunnel after login fixes the problem until next boot.

There's a system level option inside config file "delay = yes" that from my understanding delays DNS lookup until a connection has been established. After trying this a few times have established (on my system anyway) that this doesn't have any baring on it.

There must be someone on this forum that has had the same problem and solved it or someone that is more familiar with stunnel that can help.

Anyone?

---

### Post by gmargo on 2010-04-12
If it depends on the network coming up, you can put a script in **/etc/network/if-up.d/** that will be run after the network is up.  See the scripts there, and more examples in **/usr/share/doc/ifupdown/examples/**.

---

### Post by new_tolinux on 2010-04-12
> **gmargo said:**
> If it depends on the network coming up, you can put a script in **/etc/network/if-up.d/** that will be run after the network is up.  See the scripts there, and more examples in **/usr/share/doc/ifupdown/examples/**.
That does only partly make sense to me.

Wireless is disabled by a hardware-switch, I'm using eth0 (wired) which does switch on at boot, because I'm able to reach the machine through putty.

Seems a big bug to me if a tunneling-package wants to start before the default ethernet-modules are loaded.

But I'll look into it tonight.

---

### Post by new_tolinux on 2010-06-03
As I decided to remove the only job that used this tunnel after  installing 9.10, I won't put any more effort in solving this problem.  Therefore I'll marked it as solved.

---

