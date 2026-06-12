---
title: "Command for internet access times"
date: 2011-07-29
forum: General Help
---

### Post by tech291083 on 2011-07-29
Hi,

The last command shows successful log-ins by user, but is there a command that can be used to know when the internet was accessed last time? Is there a log of internet connections made by the user? Thanks

---

### Post by bodhi.zazen on 2011-07-29
What do you mean by "the internet" and what is it you want to track ?

iptables -A OUTPUT -m owner --uid-owner 1000 -j LOG

see man iptables

If that is not what you want, be more specific please. For example you can use your router, a proxy (squid), all sorts of things.

---

### Post by tech291083 on 2011-07-29
> **bodhi.zazen said:**
> What do you mean by "the internet" and what is it you want to track ?

iptables -A OUTPUT -m owner --uid-owner 1000 -j LOG




Thanks.

I would love to see something like this which is basically output of the last command. I do not want to track anything in particular, but just want to see the log-in attempts. I am not looking at this from a system admin's or security point of view at all.

```

[root@localhost ~]# last
root     pts/2                         Fri Jul 29 15:38 - 15:38  (00:00)
root     pts/1                         Fri Jul 29 12:52 - down   (02:46)
root     :0                            Fri Jul 29 12:52 - 15:39  (02:46)
reboot   system boot  2.6.15-1.2054_FC Fri Jul 29 12:50          (02:48)
root     pts/2                         Fri Jul 29 09:57 - 09:57  (00:00)
root     pts/1                         Fri Jul 29 07:56 - 09:58  (02:01)
root     :0                            Fri Jul 29 07:56 - 09:58  (02:01)
reboot   system boot  2.6.15-1.2054_FC Fri Jul 29 07:52          (02:05)

```

---

### Post by bodhi.zazen on 2011-07-29
Log in attempts to what server ?

log in attempts will be in your logs

[http://blog.bodhizazen.net/linux/ssh-logs-as-a-honeypot/](http://blog.bodhizazen.net/linux/ssh-logs-as-a-honeypot/)

---

### Post by tech291083 on 2011-07-29
> **bodhi.zazen said:**
> Log in attempts to what server ?

log in attempts will be in your logs


Sorry, I made a mistake. Log-in attempts to no server at all, I am not too technical either. All I want to see is just a list of the internet connections made by me on my personal pc, just as the last command tells me when I started the system and how long I used it for. Simple.

---

