---
title: "Change VSFTPD port"
date: 2012-05-06
forum: General Help
---

### Post by resting on 2012-05-06
I'm trying to assign a custom port to vsftp.
i added the following in /etc/vsftpd.conf
```
listen_port=2122
```


Also added an entry to iptables with:
```
sudo iptables -A INPUT -p all --dport 2122 -j ACCEPT
```

But I still couldn't connect with FileZilla. 

If I flush the iptables with 
```
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

It connects.

How do I proceed from here? I guess the rules for iptables was wrong?

---

