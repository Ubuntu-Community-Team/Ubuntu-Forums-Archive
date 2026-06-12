---
title: "Internet connection"
date: 2006-03-05
forum: General Help
---

### Post by Death on 2006-03-05
This is my first time using linux. I have read through these forums to try to find answers but nothing seems to work for me. I just cant connect.

ping 1 [www.ubuntu.com](www.ubuntu.com)
ping: unknown host [www.ubuntu.com](www.ubuntu.com)

telnet [www.google.com](www.google.com) 80
telnet: could not resolve [www.google.com/80:](www.google.com/80:) temporary failure in name resolution

sudo ifup eth0
ifup: interface eth0 already configured

ps -ef | grep dhclient3
admin 12456 12322 0 20:22 pts/0   00:00:00 grep dhclient3

cat /etc/network/interfaces
iface eth0 inet static
address 192.168.0.0
netmask 255.255.255.0
gateway 192.168.0.1
auto eth0

Any assistance would be great. Thank you.

---

### Post by suRoot on 2006-03-05
What's in /etc/resolv.conf?

```
sudo gedit /etc/resolv.conf
```

(resolv.conf is the file that has your name server info)

If it's empty or wrong, add your name server - for example:

```
nameserver 192.168.122.1
```

DHCP should update resolv.conf automatically.  Maybe it isn't on your machine, though.

---

### Post by Death on 2006-03-05
No nameserver was listed. I added exactly what you wrote but it still fails to connect. Is this a specific number or something? (truly has no clue).
Thank you.

---

### Post by jamesr on 2006-03-05
> nameserver 192.168.122.1 
That was only an example but will not work because it is on a private network. You will need to find on your isp home page, their DNS servers/nameservers and enter them.

as an additional check try the following
```
ping www.google.com
ping 72.14.203.99
```

Also in your static address, I would not use 0 eg address 192.168.0.0 I would normally higher address eg address 192.168.0.10. or use DHCP if your router  is capable. 0 is normally related to the network reference not an address.

---

### Post by njzillest on 2006-03-05
... cant help you.. 


but you might be able to help me lol..



i cant telnet due to my isp.. 
'

are you able to telnet because of your isp? or do you have a unix shell?

---

### Post by Randomskk on 2006-03-05
type "route" into a console and paste the output, if pinging google's IP fails.
If you can't ping anything, there's a chance you don't have a default route set. 

Alternatively, if you have IPv6 enabled on your network card, your router may not like it and so not process it.

---

### Post by jdp on 2006-03-05
I would nearly bet money that using 192.168.0.0 as your machine address is the problem.  ;) You should use addresses in the range of .1 to .254 as .0 and .255 are reserved. Generally, addresses that end in .0 are [subnet masks](http://en.wikipedia.org/wiki/Subnet_address).  They refer to the netowrk itself.  Actual devices start at .1 and go to .254 or so, depending on the particular setup/division of the subnet.  .255 is the "broadcast" address.

Try changing your static IP to .2 or higher, and only use the .0 as a part of the subnet mask, eg. 255.255.0.0 for a 192.168.0.0 based address.  You might even just dropt he subnet to 255.255.255.0 to just have the last dot-quad available as assignable machine numbers.

---

### Post by jdp on 2006-03-06
To add a bit more info: depending on the router setup, it might be that the DNS is pointing to the router, and the router asks the ISP DNS server for the info.  For my WiFi router setup, my machine doesn't set the actual DNS IPs, they're left blank, and the machines ask the router to pass DNS requests to where ever it's been told to by the DSL modem.  Also, depending on the router setup, it might not route certain addresses.  In my setup, the router assigns DHCP IPs in the range of 192.168.1.(2-100) and 192.168.1.(101-254) are for static.  You should check the routers configs to be sure you are using an addy in hte right range, or try using DHCP if it's not totally important to use static IPs.

---

### Post by nominal on 2006-03-06
Try system-->admin--->networking...then config your ethernet. Thats what i had to do and my connection works.

---

