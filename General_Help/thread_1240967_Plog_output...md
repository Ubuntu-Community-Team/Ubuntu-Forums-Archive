---
title: "Plog output.."
date: 2009-08-15
forum: General Help
---

### Post by karthick87 on 2009-08-15
This is my output of plog command,
karthick@karthick:~$ plog
Aug 15 20:56:15 karthick pppd[3554]: CHAP authentication succeeded: Authentication success,Welcome!
Aug 15 20:56:15 karthick pppd[3554]: CHAP authentication succeeded
Aug 15 20:56:15 karthick pppd[3554]: peer from calling number 00:E0:FC:60:40:AA authorized
Aug 15 20:56:15 karthick pppd[3554]: replacing old default route to eth0 [192.168.1.1]
Aug 15 20:56:15 karthick pppd[3554]: Cannot determine ethernet address for proxy ARP
Aug 15 20:56:15 karthick pppd[3554]: local  IP address 59.96.23.130
Aug 15 20:56:15 karthick pppd[3554]: remote IP address 59.96.22.1
Aug 15 20:56:15 karthick pppd[3554]: primary   DNS address 218.248.255.193
Aug 15 20:56:15 karthick pppd[3554]: secondary DNS address 218.248.240.79

It shows Cannot determine ethernet address for proxy ARP,what it mean??

---

### Post by juicyoner on 2009-09-02
I created a thread about this issue. I assume you are trying to connect to a pptp vpn network?

No answers yet from the ubuntu Gods

---

### Post by karthick87 on 2009-09-09
Bump.

---

### Post by BslBryan on 2009-09-09
Hello. :-)

Try to take the option below out of your wvdial script in /etc/ppp/peers.
```
gksudo gedit /etc/ppp/peers
```
And remove

```

usepeerdns
```

Then change your resolv.conf to your ISP's DNS servers and restart ppd.  

Also, you might want to take a look [here.]("http://kutuma.blogspot.com/2007/05/vpn-in-ubuntu.html")

---

### Post by karthick87 on 2009-09-09
when i execute this in terminal i get the error..

karthick@Learners-desktop:~$ gksudo gedit /etc/ppp/peers
No protocol specified
(gedit:3714): Gtk-WARNING **: cannot open display: :0.0

---

