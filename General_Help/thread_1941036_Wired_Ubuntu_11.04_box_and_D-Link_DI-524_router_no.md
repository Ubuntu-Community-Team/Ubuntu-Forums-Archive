---
title: "Wired Ubuntu 11.04 box and D-Link DI-524 router: no connection to the internet"
date: 2012-03-14
forum: General Help
---

### Post by Fausto Arinos Barbuto on 2012-03-14
Hi,

My old Belkin router toasted and then I bought a D-Link DI-524. I have a domestic network with a wireless laptop (W7-64 bit), a desktop (Vista-32) and a second desktop with Ubuntu 11.04. The two Windows machines promptly recognized the new router and connected to the internet, whereas the Ubuntu machine did not.

Curiously, the 11.04 machine got a valid IP from the router and can see the other two Windows computers' shared folders; and these latter two, by their turn, can see 11.04's public (shared) folder. Hence, the Ubuntu box has some connectivity, yet local only. What should I do so that this box can connect to the internet? Please help me -- I suspect I'm a few steps away from a successful connection to the internet, but I simply don't know what to do. Just a quick reminder: the Ubuntu desktop is a wired one, not wireless.

Thanks in advance for any help!

F.

---

### Post by lrgmmc on 2012-03-15
did you set your ip manually? If so did you make sure to add the proper dns servers.

---

### Post by Fausto Arinos Barbuto on 2012-03-15
> **lrgmmc said:**
> did you set your ip manually? If so did you make sure to add the proper dns servers.

I chose dynamic IP and did not set any DNS servers.

I've made a little progress though: I learnt that the following command:

**[COLOR="Navy"]sudo dhclient3 eth0[/COLOR]**

opens the access to the internet.  I don't know why, however.  Also, this command doesn't stick: if I reboot the machine the internet connection goes away again.  I must find how to keep my connection active.

Thanks for your reply.

F.

---

### Post by lrgmmc on 2012-03-15
could you post your network config file. 
```
cat /etc/network/interfaces
```

---

### Post by Fausto Arinos Barbuto on 2012-03-15
> **lrgmmc said:**
> could you post your network config file. 
```
cat /etc/network/interfaces
```

Sure, here it goes:

[COLOR="Navy"]auto lo
iface lo inet loopback[/COLOR]

That's all about it, only two lines...

Thanks,

Fausto

---

### Post by Fausto Arinos Barbuto on 2012-03-15
Problem solved.  I changed my /etc/network/interfaces and now it reads:

[COLOR="Navy"]auto eth0
iface eth0 inet dhcp
[/COLOR]

Thanks a lot to everyone.

F.

---

