---
title: "iptables and SAMBA?"
date: 2006-03-30
forum: General Help
---

### Post by crixtiano on 2006-03-30
Please, how to free SAMBA using iptables?

I have 2 PCs: 172.20.0.1 and 172.20.0.2

how to free 172.20.0.2 "to see"  172.20.0.1 ?

---

### Post by seppo on 2006-03-30
On your samba server adjust the inbound rule. You can do this by allowing your local subnet to connect on all ports:

> iptables -A INPUT -s 172.20.0.0/24 -j ACCEPT

Asuming your subnet mask is 255.255.255.0

You can also allow specific ip's or ports, see the man pages for more detail.

---

### Post by crixtiano on 2006-03-30
[QUOTE=seppo]On your samba server adjust the inbound rule. You can do this by allowing your local subnet to connect on all ports:



Asuming your subnet mask is 255.255.255.0

You can also allow specific ip's or ports, see the man pages for more detail.[/QUOTE]

Hi, my iptables chains are for this IP:


sudo iptables -A INPUT -s 172.20.0.0/255.255.0.0 -j ACCEPT
sudo iptables -A OUTPUT -d 172.20.0.0/255.255.0.0 -j ACCEPT

#DNS server
sudo iptables -t nat -A POSTROUTING -s 172.20.0.0/16 -d $IP_DNS -o wlan0 -j MASQUERADE
sudo iptables -A FORWARD -s 172.20.0.0/16 -d $IP_DNS -p udp --dport 53 -j ACCEPT
sudo iptables -A FORWARD -s $IP_DNS -d 172.20.0.0/16 -p udp --sport 53 -j ACCEPT

#HTTP services
sudo iptables -A FORWARD -s 172.20.0.0/16 -p tcp --dport 80 -j ACCEPT
sudo iptables -A FORWARD -d 172.20.0.0/16 -p tcp --sport 80 -j ACCEPT
sudo iptables -A FORWARD -s 172.20.0.0/16 -p tcp --dport 443 -j ACCEPT
sudo iptables -A FORWARD -d 172.20.0.0/16 -p tcp --sport 443 -j ACCEPT

#NAT
sudo iptables -t nat -A POSTROUTING -s 172.20.0.0/16 -o wlan0 -j MASQUERADE

and it doesn't work.

---

### Post by seppo on 2006-03-30
Are you sure that samba is listening on the external interface? 

Post your whole iptables listing, maybe there is a rule up denying access

---

### Post by crixtiano on 2006-03-30
[QUOTE=seppo]Are you sure that samba is listening on the external interface? 

Post your whole iptables listing, maybe there is a rule up denying access[/QUOTE]

Yes, if I open all, SAMBA works fine:

sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -t nat -A POSTROUTING -s 172.20.0.0/16 -o wlan0 -j MASQUERADE

but if I Drop everithing and free what I need, it doesn't work

---

### Post by halfvolle melk on 2006-03-30
I think Samba works on 137:139. What if you set up rules for those?

---

