---
title: "password problems 10.04 Lucid, unable to connect to 192.168.1.254 &amp; wireless"
date: 2011-09-18
forum: General Help
---

### Post by Vpc on 2011-09-18
I can see the password for the wireless network in the Network Manager is correct but NM keeps on trying to connect without any success (the NM icon keeps showing the animation indicating that it's trying to connect). I think this is related to the fact that I when I try to access [http://192.168.1.254/](http://192.168.1.254/) to check out the configuration for my wired internet (as instructed by my wired ISP) it continues to prompt me for my password after I enter it. I have confirmed with my wired ISP that I had the correct username and password. So I think there may be a problem with transmitting passwords overall. 

Don't know if this helps, but my hostname:
```

administrator@snoopy:~$ more /etc/hostname
snoopy

administrator@snoopy:~$ more /etc/hosts
127.0.0.1 localhost
127.0.1.1 snoopy

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Any ideas? Can it be solved by modifying the password keyring?

---

