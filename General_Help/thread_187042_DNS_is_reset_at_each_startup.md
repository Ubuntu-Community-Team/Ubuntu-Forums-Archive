---
title: "DNS is reset at each startup"
date: 2006-06-02
forum: General Help
---

### Post by sanderjd on 2006-06-02
For whatever reason, my DNS servers are detected improperly and must be entered manually. This is a huge annoyance, but I've gotten over it because now I just have the numbers memorized. However, after installed Dapper, the DNS numbers that I have entered manually are reset every time I restart. Does anybody know a way to keep these from being changed all the time?

---

### Post by fluid_motion on 2006-06-04
I am facing the same issue as well ever since upgrading to dapper final.  Whenever I startup Ubuntu the DNS server settings are cleared and I have to manually input them. I am using static ip setup. This did not happen in Dapper beta or RC. Anybody got a fix?

---

### Post by professor_chaos on 2006-06-04
I and others have posted on this forum of a method to "lock" /etc/resolv.conf so that your addresses will not be changed. 
This is what I had to do, back in my breezy days, so I dont think is specific to dapper. 
Do a search on this forum with the two keywords "chattr resolv.conf".
The method is below.

First edit the file /etc/resolv.conf and then...

```
sudo chattr +i /etc/resolv.conf
```

this will prevent changing of the file. To unlock the file use...

```
sudo chattr -i /etc/resolv.conf
```

---

### Post by Nech on 2006-06-05
I can't :(

root@eclosio:~# chattr +i /etc/resolv.conf
chattr: The operation ioctl () is not adapted to the device  while reading flags on /etc/resolv.conf

root@eclosio:~# chattr +i /etc/resolvconf/run/resolv.conf
chattr: The operation ioctl () is not adapted to the device while reading flags on /etc/resolvconf/run/resolv.conf

---

### Post by JamesB on 2006-06-05
[QUOTE=sanderjd]For whatever reason, my DNS servers are detected improperly and must be entered manually. This is a huge annoyance, but I've gotten over it because now I just have the numbers memorized. However, after installed Dapper, the DNS numbers that I have entered manually are reset every time I restart. Does anybody know a way to keep these from being changed all the time?[/QUOTE]

As a temp solution a edited /etc/dhcp3/dhclient.conf
prepend domain-name-servers <IP-FOR-YOUR-DNS-SERVER> (removing the #) and deleting 'domain-name-servers' from the request line 

Mine looks like this:

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 212.74.112.66, 212.74.112.67;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;

Hope this helps

---

### Post by _simon_ on 2006-06-05
If you use a router then you can add your DNS in there.

---

### Post by murdochdutchie on 2006-06-17
I am also having this issue, i am running on DHCP because for some reason Ubuntu networking does not function right if i use my wireless(eg it can't find the network resources anymore)., so how do i get Ubuntu to remember my dns settings if i am on dhcp?

---

### Post by scxtt on 2006-06-17
DNS should be detected by the router, then passed on to your box ... can you check your settings on the router?

---

