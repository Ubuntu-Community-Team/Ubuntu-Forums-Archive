---
title: "Firewall-Problem-Ubuntu"
date: 2010-06-26
forum: General Help
---

### Post by Maximus20 on 2010-06-26
Hello guys...lets cut to the problem...this morning i've deleted accidentaly my ubuntu username...thats not really the problem...when i've done that...the directory with all folders and files were deleted too...nothing went wrong after that...but when i rebooted my pc...and i tried to start my firewall...running on ipv4 the following error appeared :
```
root@hosting-desktop:~# ./firewall.sh
: command not found 2:
: command not found 3:
: No such file or directoryn/modprobe
: No such file or directoryin/modprobe
: command not found 14:
: No such file or directoryoc/sys/net/ipv4/tcp_fin_timeout
: No such file or directoryoc/sys/net/core/netdev_max_backlog
: No such file or directoryoc/sys/net/core/somaxconn
: No such file or directoryoc/sys/net/ipv4/tcp_keepalive_time
: No such file or directoryoc/sys/net/ipv4/tcp_keepalive_intvl
: No such file or directoryoc/sys/net/ipv4/tcp_keepalive_probes
: No such file or directoryoc/sys/net/ipv4/tcp_syncookies
: No such file or directoryoc/sys/net/ipv4/tcp_synack_retries
: No such file or directoryoc/sys/net/ipv4/tcp_syn_retries
: No such file or directoryoc/sys/net/ipv4/tcp_max_syn_backlog
./firewall.sh: line 33: /proc/sys/net/ipv4/netfilter/ip_conntrack_generic_timeou: No such file or directory
: No such file or directoryoc/sys/net/ipv4/conf/all/rp_filter
: No such file or directoryoc/sys/net/netfilter/nf_conntrack_max
: No such file or directoryoc/sys/net/ipv4/tcp_window_scaling
: No such file or directoryoc/sys/net/ipv4/tcp_sack
: No such file or directoryoc/sys/net/ipv4/conf/all/accept_source_route
: No such file or directoryoc/sys/net/ipv4/icmp_echo_ignore_broadcasts
: No such file or directoryoc/sys/net/ipv4/icmp_ignore_bogus_error_responses
: No such file or directoryoc/sys/net/ipv4/conf/all/log_martians
: No such file or directoryoc/sys/net/ipv4/tcp_timestamps
: No such file or directoryoc/sys/net/core/rmem_max
: No such file or directoryoc/sys/net/core/wmem_max
: No such file or directoryoc/sys/net/ipv4/tcp_rmem
: No such file or directoryoc/sys/net/ipv4/tcp_wmem
: No such file or directoryoc/sys/net/ipv4/tcp_no_metrics_save
: No such file or directoryoc/sys/net/ipv4/ip_local_port_range
: command not found 55:
'/firewall.sh: line 57: syntax error near unexpected token `{
'/firewall.sh: line 57: `    protect_hub(){
```

But there is one more problem...those directorys exist...don't know whats the real problem in this because with my original username when i've installed ubuntu 8.04 this firewall worked...btw my username was hosting...anyway if you guys can help me with something...please...

Thanks in advance .

---

### Post by bodhi.zazen on 2010-06-26
I have no idea, but I am guessing you deleted the firwall script.

Is there some reason you do not use UFW or use iptables directly ?

You can try downloading and re-installing firewall.sh, wherever you got that from.

IMO I would advise you use a different tool, I find these various "firewall scripts" are more complicated then then need to be.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by Maximus20 on 2010-06-26
```

```The firewall.sh is a anti-ddos script not a setup or things like that...anyways thanks 4 your reply .
And i've not deleted it...it can't find those dirs but they are there...don't understand the problem...

Leaving this problem behind...i have one more problem i broken /etc/sudoers because i edited it with nano instead of vi or visudo so now i need some help...tell me exactly how do i paste a text there or writing (both things with vi) without any problems .

I know that the base /etc/sudoers file is :

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

I just need somebody to help me put it there with vi or visudo . (using root account)

Thanks in advance .

---

### Post by bodhi.zazen on 2010-06-27
If sudo is broken, you will need to fix it either by booting to recovery mode or booting a live CD.

If you boot a live CD, you will need to mount your server partition and then edit the file.

As you may now know, the advantage of visudo is that it (helps) prevent exactly this kind of an issue (by checking the syntax).

---

### Post by Maximus20 on 2010-06-27
i've solved all my problems with some terminal commands...not with the cd :D...anyways thanks again for your suport .

---

